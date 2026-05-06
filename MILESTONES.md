# RigForge AI - Detailed Milestone Plan

**Total Duration:** 10 months
**Grant Cycle:** Epic MegaGrants Cycle 2 (submitted June-September 2026)

---

## Milestone Overview

| # | Milestone | Duration | Status |
|---|-----------|----------|--------|
| 1 | Research and Prototype | Months 1-2 | Not started |
| 2 | Mechanical Segmentation and Naming | Months 3-4 | Not started |
| 3 | Rigging and Animation | Months 5-7 | Not started |
| 4 | Unreal Engine Integration | Months 8-9 | Not started |
| 5 | Open-Source Release and Community | Month 10 | Not started |

---

## Milestone 1: Research and Prototype (Months 1-2)

### Goal
Establish the foundation: asset taxonomy, sample dataset, first working Blender pipeline, basic agent orchestration.

### Deliverables
- [ ] Define supported asset taxonomy: car, drone, tank (with sub-categories)
- [ ] Collect or generate 30+ sample AI-generated models (OBJ, FBX, GLB)
- [ ] Build first Blender Python analysis script (reads mesh, identifies clusters)
- [ ] Implement component detection heuristics (symmetry, size, position, adjacency)
- [ ] Create basic agent orchestration framework (input → analysis → output)
- [ ] First Unreal Engine import test with cleaned model
- [ ] Write research notes documenting findings and failure modes
- [ ] Set up CI/CD pipeline for automated testing

### Success Criteria
- At least 10 sample models processed through basic analysis
- Detection heuristics correctly identify object type on at least 60% of samples
- First Blender add-on runs without errors on sample models
- First model successfully imported into Unreal Engine

### Technical Notes
- Evaluation framework to be built alongside pipeline
- Sample dataset should include both "easy" (clean geometry) and "hard" (fused parts) examples
- Document failure cases for future agent improvement

---

## Milestone 2: Mechanical Segmentation and Naming (Months 3-4)

### Goal
Achieve reliable component separation, semantic naming, pivot correction, and scale normalization.

### Deliverables
- [ ] Component grouping algorithm (mesh island detection + heuristics + AI classification)
- [ ] Semantic naming system (wheel_FL, wheel_FR, wheel_RL, wheel_RR, body, door_L, etc.)
- [ ] Hierarchy cleanup (correct parent-child relationships)
- [ ] Pivot placement for each component type (wheel center, door hinge, turret base)
- [ ] Scale normalization to real-world units (Unreal cm-based)
- [ ] First automated validation report (JSON + human-readable)
- [ ] Test suite for segmentation accuracy

### Success Criteria
- Component separation correct on at least 70% of car test assets
- Component separation correct on at least 70% of drone test assets
- Component separation correct on at least 60% of tank test assets (harder due to track complexity)
- Pivot placement correct on at least 70% of detected moving parts
- Scale normalization within 5% of expected real-world dimensions

### Component Naming Convention
- Wheels: wheel_FL, wheel_FR, wheel_RL, wheel_RR (front-left, front-right, rear-left, rear-right)
- Drone rotors: rotor_FL, rotor_FR, rotor_RL, rotor_RR
- Tank: turret, barrel, track_L, track_R, wheel_[L/R]_[01-08]
- Generic: body, chassis, door_L, door_R, hood, trunk, landing_gear_[L/R/N]

---

## Milestone 3: Rigging and Animation (Months 5-7)

### Goal
Create animation-ready rig structures and generate base animation clips for all supported asset types.

### Deliverables

#### Wheeled Vehicles
- [ ] Wheel rotation rig (spin axis, speed-linked rotation)
- [ ] Steering rig (front wheel turn angle, Ackermann-approximate)
- [ ] Suspension rig (vertical travel per wheel, body roll)
- [ ] Door hinge rig (open/close animation)

#### Flying Mechanical Assets
- [ ] Propeller/rotor spin rig (individual and collective)
- [ ] Blade pitch animation (for helicopters)
- [ ] Landing gear retract/extend rig
- [ ] Fuselage flex (optional, for larger aircraft)

#### Tracked/Turreted Vehicles
- [ ] Turret rotation rig (horizontal pan)
- [ ] Barrel elevation rig (vertical tilt)
- [ ] Track animation (loop texture or bone-driven)
- [ ] Hatch open/close rig

#### Base Animation Clips (all types)
- [ ] Idle (engine shake, rotor idle)
- [ ] Moving forward (wheels spin, tracks move)
- [ ] Turning (steering wheels angle)
- [ ] Special action (door open, turret aim, propeller spool up)

### Success Criteria
- All three asset families have working base animation clips
- Animations import correctly into Unreal Engine without retargeting
- Blueprint or AnimBP can drive animations from runtime parameters (speed, turn angle)
- At least one full vehicle demo scene working in Unreal

---

## Milestone 4: Unreal Engine Integration (Months 8-9)

### Goal
Complete the pipeline from AI-generated model to fully functional Unreal Engine asset with Blueprint control.

### Deliverables
- [ ] Unreal import automation script (Python or Blueprint utility)
- [ ] Blueprint generation utility (PhysicsVehicle or custom Blueprint per asset type)
- [ ] Chaos Vehicle Physics setup for wheeled vehicles (or custom physics)
- [ ] Collision mesh generation (per-component simplified collision)
- [ ] LOD stub generation (LOD0 complete, LOD1-3 placeholder)
- [ ] Material assignment automation (slot mapping from Blender to Unreal)
- [ ] Test map: wheeled vehicle driving demo
- [ ] Test map: drone flying demo
- [ ] Test map: tank with turret aim demo
- [ ] Playable demo scene with all three asset types
- [ ] Asset readiness report generated per asset

### Unreal Asset Checklist (per asset)
- [ ] Mesh imports without errors
- [ ] Hierarchy preserved in Unreal
- [ ] Pivots correct after import
- [ ] Scale correct (Unreal units = cm)
- [ ] Animations assigned and preview correctly
- [ ] Collision meshes attached
- [ ] Blueprint controls work
- [ ] Physics simulate correctly

### Success Criteria
- All three demo assets playable in Unreal Engine without manual setup
- Zero required manual adjustments to hierarchy, pivots, or scale
- Blueprint exposes: speed, turn, turret direction, door open, rotor speed
- Demo video recorded showing all three assets in motion

---

## Milestone 5: Open-Source Release and Community (Month 10)

### Goal
Release all tools, documentation, and assets publicly. Engage the Unreal and Blender communities.

### Deliverables
- [ ] GitHub repository fully documented (this repo)
- [ ] Blender add-on packaged and released (installable .zip)
- [ ] Unreal Engine plugin or import scripts packaged
- [ ] Example assets released (3 cleaned + rigged assets per category = 9 assets total)
- [ ] Benchmark dataset released (raw AI-generated inputs + expected outputs)
- [ ] Full documentation: installation, usage, agent architecture, contributing guide
- [ ] Tutorial videos: one per asset type (car, drone, tank)
- [ ] Blog post / announcement for Unreal Engine and Blender communities
- [ ] Community feedback channel (GitHub Discussions or Discord)
- [ ] Roadmap published for future development (tracked vehicles, aircraft, robots)

### Community Targets
- GitHub repository with clear README and contribution guide
- Post in Unreal Engine forums (MegaGrants success story + tool announcement)
- Post in Blender Artists / Blender Community forums
- Share on relevant subreddits (r/unrealengine, r/blender, r/gamedev)
- Submit to awesome-unreal and similar community lists

---

## First 90-Day Execution Plan

### Days 1-30 (Month 1)
- Set up development environment (Blender, Unreal, Python, Git)
- Create sample dataset from public AI-generated model sources
- Write first Blender analysis script (mesh cluster detection)
- Define component taxonomy document
- Run first import test into Unreal Engine
- Set up automated test framework

### Days 31-60 (Month 2 - Month 3 bridge)
- Implement segmentation logic with AI classification
- Add pivot detection and placement
- Add wheel/propeller/turret movement architecture
- Run against full 30-asset test set
- Generate first validation report
- Record first before/after demo (rough version)

### Days 61-90 (Month 3)
- Add Unreal Blueprint automation
- Build first working demo map
- Package alpha release of Blender add-on
- Record polished MegaGrants demo video
- Publish GitHub repository with documentation
- Submit to Epic MegaGrants (if within window)

---

*RigForge AI - Milestone Plan v1.0 - May 2026*
