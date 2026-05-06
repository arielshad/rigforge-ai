# RigForge AI - Technical Architecture

**Version:** 1.0 (Pre-Development)
**Date:** May 2026

---

## System Overview

RigForge AI is a multi-agent pipeline that transforms raw AI-generated 3D mechanical models into production-ready Unreal Engine assets. The system consists of 9 specialized agents coordinated by an orchestration layer, with Blender as the primary mesh processing environment and Unreal Engine as the output target.

---

## High-Level Architecture

    AI-Generated 3D Model
    (OBJ / FBX / GLB / USD)
            |
            v
    +-----------------------+
    |   Ingestion Layer     |  File format parsing, initial validation
    +-----------------------+
            |
            v
    +-----------------------+
    | Agent Orchestrator    |  Coordinates agent sequence, handles errors
    +-----------------------+
            |
       +---------+
       |         |
       v         v
    [Agent 1]  [Agent 2]  ... [Agent 9]    (run sequentially or in parallel)
       |
       v
    +-----------------------+
    |   Blender Runtime     |  All mesh operations happen in Blender
    +-----------------------+
            |
            v
    +-----------------------+
    |   Unreal Export Layer |  FBX/glTF/USD export + Unreal import automation
    +-----------------------+
            |
            v
    Unreal Engine Asset
    (Mesh + Rig + Animations + Blueprint + Collision)

---

## The 9 Agents

### Agent 1: Asset Analysis Agent

**Purpose:** Understand what the input model is before doing anything to it.

**Inputs:** Raw 3D model file
**Outputs:** Asset type classification, complexity score, preliminary component map

**Approach:**
- Render model from multiple angles (front, side, top, isometric)
- Pass renders to a vision-language model (e.g., GPT-4V, Gemini Vision, or open equivalent)
- VLM returns: asset type (car/drone/tank/aircraft/robot/unknown), confidence score, observable features
- Supplement with geometric heuristics: overall dimensions, number of mesh islands, symmetry score

**Asset Types Supported (v1):**
- Wheeled Vehicle (car, truck, jeep, APC)
- Flying Mechanical (drone, helicopter, aircraft)
- Tracked/Turreted (tank, sci-fi mech)

---

### Agent 2: Component Segmentation Agent

**Purpose:** Split the monolithic model into meaningful, separable parts.

**Inputs:** Raw model + asset type classification from Agent 1
**Outputs:** Segmented mesh with labeled component groups

**Approach:**
- Mesh island detection (separate disconnected geometry)
- Geometric analysis: position, size, symmetry, proximity to other components
- Type-specific heuristics (for a car: 4 wheel-sized spherical objects at corners = wheels)
- VLM assistance for ambiguous cases (screenshot-based)
- Blender Python: bpy.ops.mesh.separate() to split by loose parts

**Component Types by Asset Family:**

Car/Truck: body, wheel_FL, wheel_FR, wheel_RL, wheel_RR, door_L, door_R, hood, trunk, axle_F, axle_R

Drone: body, rotor_FL, rotor_FR, rotor_RL, rotor_RR, landing_gear_L, landing_gear_R, landing_gear_N, camera

Tank: body, turret, barrel, track_L, track_R, wheel_L_01..08, wheel_R_01..08, hatch

---

### Agent 3: Semantic Naming Agent

**Purpose:** Give every component a clean, predictable, semantic name.

**Inputs:** Segmented mesh with labeled groups
**Outputs:** Model with clean object names and organized hierarchy

**Naming Convention:**
- Format: [AssetName]_[ComponentType]_[Position/Index]
- Example: Truck_Wheel_FL, Tank_Turret, Drone_Rotor_FR
- Hierarchy: Asset root > Category groups > Individual components

**Blender Operations:**
- Rename objects via bpy.data.objects[...].name
- Create empty parent objects for logical grouping
- Set custom properties for metadata

---

### Agent 4: Pivot and Transform Agent

**Purpose:** Place correct origins and rotation axes for every moving part.

**Inputs:** Named, segmented model
**Outputs:** Model with corrected origins and rotation axes

**Pivot Rules by Component Type:**
- Wheel: center of wheel, rotation axis = local X (for forward spin)
- Steering wheel: center, rotation axis = local Z
- Turret: base center on body surface, rotation axis = world Z
- Barrel: hinge point at turret attachment, rotation axis = local Y (elevation)
- Propeller: shaft center, rotation axis = local Z
- Door: hinge edge midpoint, rotation axis = local Z or Y depending on door axis
- Landing gear: pivot at attachment point, rotation axis for retraction

**Blender Operations:**
- bpy.ops.object.origin_set(type='ORIGIN_CURSOR') after placing cursor
- Manual pivot calculation based on bounding box and component type
- Scale, rotation, and location application (apply transforms)

---

### Agent 5: Rigging Agent

**Purpose:** Create control rigs or bone structures to drive mechanical animation.

**Inputs:** Model with correct pivots
**Outputs:** Armature or control rig linked to mesh components

**Approach Options:**
Option A: Bone-based armature (for Unreal Skeletal Mesh)
Option B: Control rig with constraint-driven animation (for Blender-native workflow)
Option C: Empty-object parent rig (lightweight, for rigid body animation)

**For MVP (Option C - simplest):**
- Create Empty parent objects at pivot locations
- Parent mesh components to Empties
- Empties become animation channels
- Animatable via F-Curves in Blender
- Importable into Unreal as bone hierarchy (converted at export)

**Rig Structures by Asset:**
- Car: Wheel empties x4, Suspension empty x4, SteeringPivot empty x2, BodyRoot
- Drone: RotorPivot x4, LandingGearPivot x2, BodyRoot
- Tank: TurretPivot, BarrelPivot, TrackOffset_L, TrackOffset_R, BodyRoot

---

### Agent 6: Physics and Collision Agent

**Purpose:** Create collision meshes and physics constraints for runtime behavior.

**Inputs:** Rigged model
**Outputs:** Model with collision meshes and physics metadata

**Collision Types:**
- Box collision: doors, hood, trunk, flat panels
- Sphere collision: wheels, ball joints
- Capsule collision: barrels, axles, cylindrical parts
- Convex hull: complex body shapes
- Per-poly: only for very small detailed parts

**Physics Metadata (Custom Properties):**
- Mass estimates per component (kg)
- Friction coefficients
- Wheel radius and width
- Suspension travel distance
- Constraint limits (turret rotation range, barrel elevation range)

**Unreal-Specific Output:**
- UCX_ prefix naming for Unreal collision meshes
- PhysicsAsset-compatible bone structure
- Wheel radius values for Chaos Vehicle Physics

---

### Agent 7: Animation Agent

**Purpose:** Generate base animation clips for each asset type.

**Inputs:** Rigged model with physics metadata
**Outputs:** Base animation clips (NLA tracks in Blender, FBX animation sequences for Unreal)

**Standard Clips per Asset Type:**

Wheeled Vehicle:
- Wheel_Spin (continuous loop, 1 rotation = vehicle circumference travel)
- Wheel_Steer_Left, Wheel_Steer_Right (max steering angle)
- Suspension_Bounce (idle oscillation)
- Door_Open, Door_Close

Drone:
- Rotor_Idle (slow spin)
- Rotor_Flight (fast spin)
- LandingGear_Retract, LandingGear_Deploy
- Takeoff_Hover (body rise + rotor spool)

Tank:
- Turret_Rotate_Full (0 to 360 degrees)
- Barrel_Elevate_Up, Barrel_Elevate_Down
- Hatch_Open, Hatch_Close
- Track_Roll_Forward (looping track movement)

**Implementation:**
- Blender F-Curves for each animation channel
- NLA editor for clip organization
- Export as separate FBX animation files or embedded in main FBX

---

### Agent 8: Unreal Export Agent

**Purpose:** Export the finished asset in Unreal-compatible format and automate the import process.

**Inputs:** Fully rigged and animated model
**Outputs:** Unreal Engine project with imported asset, Blueprint, and test setup

**Export Settings (FBX):**
- Scale: 100x (Blender meters to Unreal centimeters)
- Forward: -Z Forward, Up: Y Up (Unreal convention)
- Apply modifiers: Yes
- Armature: Include deform bones only
- Animation: Include all NLA tracks as separate sequences

**Unreal Import Automation (Python):**
- unreal.AssetImportTask() for mesh import
- unreal.FbxImportUI() for import settings
- unreal.AnimSequenceImportData() for animation import
- Auto-create LOD group stub
- Auto-assign default material instances

**Blueprint Generation:**
- Template BP_Vehicle_Base (for wheeled vehicles)
- Template BP_Drone_Base (for flying assets)
- Template BP_Tank_Base (for tracked vehicles)
- Auto-wire animation variables to runtime parameters (speed, turn angle, etc.)

---

### Agent 9: Validation Agent

**Purpose:** Run automated checks to verify the asset is truly production-ready.

**Inputs:** Imported Unreal asset
**Outputs:** JSON validation report + human-readable summary

**Validation Checklist:**

Mesh Checks:
- [ ] No overlapping geometry at component seams
- [ ] No inverted normals on visible surfaces
- [ ] UV maps present on all visible meshes
- [ ] LOD0 triangle count within budget (TBD by asset type)
- [ ] No n-gons on collision meshes

Hierarchy Checks:
- [ ] All expected components present by name
- [ ] Correct parent-child relationships
- [ ] No extra/unnamed objects

Transform Checks:
- [ ] Scale applied (all transforms = 1.0 in Unreal)
- [ ] Pivots at expected locations
- [ ] Asset fits expected bounding box (car: ~4.5m long, drone: ~0.5m span, tank: ~6m long)

Animation Checks:
- [ ] All expected animation clips present
- [ ] Clips are correct length (e.g., Wheel_Spin = 1 rotation / circumference)
- [ ] No animation curves at rest pose (T-pose check)

Physics Checks:
- [ ] Collision meshes present on all major components
- [ ] Wheel physics radius matches visual wheel
- [ ] Turret rotation constraint within expected range

**Report Format:**
- JSON: machine-readable for CI/CD
- Markdown: human-readable for review
- Score: 0-100 (weighted by check importance)
- Status: PASS / WARN / FAIL per check

---

## Technology Stack

| Layer | Technology | Notes |
|-------|-----------|-------|
| Mesh Processing | Blender 4.x + Python | Primary processing environment |
| Geometry Analysis | trimesh, Open3D, NumPy | For programmatic mesh analysis |
| AI / VLM | GPT-4V, Gemini Vision, or LLaVA | For visual asset understanding |
| Agent Orchestration | LangGraph or custom | Stateful agent pipeline management |
| Export Format | FBX (primary), glTF (secondary) | FBX for max Unreal compatibility |
| Unreal Automation | Unreal Python API | Import, Blueprint, setup automation |
| Validation | Custom Python + Unreal Python | JSON + Markdown reports |
| CI/CD | GitHub Actions | Automated testing on commit |

---

## Data Flow

    Input Model File
         |
         | [Ingestion]
         v
    Normalized Model (standardized scale, coordinate system)
         |
         | [Agent 1: Analysis]
         v
    Asset Metadata (type, confidence, feature map)
         |
         | [Agent 2: Segmentation]
         v
    Segmented Components (separate mesh objects)
         |
         | [Agent 3: Naming]
         v
    Named Hierarchy (clean object names, logical groups)
         |
         | [Agent 4: Pivots]
         v
    Transform-Corrected Model (applied transforms, correct pivots)
         |
         | [Agent 5: Rigging]
         v
    Rigged Model (control structure, animation channels)
         |
         | [Agent 6: Physics]
         v
    Physics-Ready Model (collision, constraints, metadata)
         |
         | [Agent 7: Animation]
         v
    Animated Model (base clips, NLA tracks)
         |
         | [Agent 8: Export]
         v
    Unreal Engine Asset (imported mesh, Blueprint, test map)
         |
         | [Agent 9: Validation]
         v
    Validation Report (JSON + Markdown, score 0-100)

---

## Known Challenges and Mitigations

| Challenge | Mitigation |
|-----------|-----------|
| AI-generated models have fused geometry | Segmentation heuristics + VLM fallback |
| VLM misclassification of unusual models | Confidence threshold + human review flag |
| FBX export scale issues | Explicit scale application at every step |
| Unreal import coordinate system mismatch | Standardized -Z Forward, Y Up convention |
| Animation retargeting for unusual rigs | Template rig structures per asset type |
| Track/caterpillar animation complexity | v1: UV scroll only; v2: bone-driven |

---

*RigForge AI - Architecture v1.0 - May 2026*
