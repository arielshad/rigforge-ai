# RigForge AI - Demo Video Script

**Target Length:** 2 minutes (120 seconds)
**Purpose:** Epic MegaGrants application video
**Format:** Screen recording with voiceover + optional captions

---

## Video Structure Overview

| Segment | Duration | Content |
|---------|----------|---------|
| 1. The Problem | 0:00 - 0:15 | Show broken AI-generated model |
| 2. The Pipeline | 0:15 - 0:45 | Agent workflow running live |
| 3. Before vs After | 0:45 - 1:30 | Side-by-side comparison |
| 4. Unreal Engine Demo | 1:30 - 2:00 | Assets running in Unreal |
| 5. Vision (optional) | 1:55 - 2:00 | Closing statement |

---

## Segment 1: The Problem (0:00 - 0:15)

### Visuals
- Import an AI-generated car model into Blender
- Show the outliner: single object, named "Mesh_001" or similar
- Zoom into wheel area: wheels fused to body
- Switch to Unreal Engine: import same model
- Attempt to rotate a wheel in Unreal: nothing moves
- Show the mess: no hierarchy, fused geometry

### Voiceover Script
"AI tools can generate impressive-looking 3D vehicles. But import them into Unreal Engine, and they break. Wheels fused to the body. No hierarchy. No pivots. No animation. No physics. A technical artist still has to fix everything manually."

### On-Screen Text
"AI-generated 3D models: impressive to look at. Impossible to use."

---

## Segment 2: The Agent Pipeline (0:15 - 0:45)

### Visuals
- Show RigForge AI terminal or UI running
- Text overlays showing each agent activating:
  - "Analyzing asset type... Vehicle detected (confidence: 94%)"
  - "Segmenting components... Found: body, 4 wheels, 2 doors, hood"
  - "Naming components... wheel_FL, wheel_FR, wheel_RL, wheel_RR"
  - "Fixing pivots... Wheel centers calculated"
  - "Building rig... Wheel spin, steering, suspension"
  - "Creating collision... UCX meshes generated"
  - "Generating animations... Wheel_Spin, Door_Open"
  - "Exporting to Unreal..."
  - "Validation: PASS (score 87/100)"

### Voiceover Script
"RigForge AI uses a pipeline of specialized agents to fix this automatically. The Asset Analysis Agent identifies the vehicle type. The Segmentation Agent separates wheels, doors, and body parts. The Naming Agent creates clean, semantic labels. The Pivot Agent places correct rotation axes. The Rigging Agent builds the animation structure. The Animation Agent generates base motion clips. And the Export Agent sends it all to Unreal Engine - ready to use."

### On-Screen Text
Animated labels appearing as each agent runs.

---

## Segment 3: Before vs After (0:45 - 1:30)

### Visuals - Split Screen

Left side: "BEFORE - Raw AI-Generated Model"
- Single mesh object
- Random name ("Mesh_001")
- Wheels fused to body
- No outliner hierarchy
- No animation clips
- Click wheel: nothing moves

Right side: "AFTER - RigForge AI Output"
- Clean hierarchy in outliner
- Names: Car_Body, Car_Wheel_FL, Car_Wheel_FR, etc.
- Wheel physically separated
- Animation clips visible: Wheel_Spin, Door_Open, Steering
- Click play: wheels rotate correctly
- Rotate car: steering wheels turn

### Vehicle Demo (0:45 - 1:00)
Show car: wheels spin with vehicle movement, doors open/close.

### Drone Demo (1:00 - 1:15)
Show drone: four propellers spin, landing gear retracts on takeoff.

### Tank Demo (1:15 - 1:30)
Show tank: turret rotates independently, barrel elevates, tracks scroll.

### Voiceover Script
"The result: a clean, structured asset ready for real-time use. On the left, the raw AI-generated model - a single unnamed mesh with no hierarchy and no animation. On the right, the same model after RigForge AI. Clean component names. Correct pivots. Working animations. Every wheel, propeller, and turret behaves exactly as expected."

---

## Segment 4: Unreal Engine Demo (1:30 - 2:00)

### Visuals
- Open Unreal Engine with demo level
- Car driving on road: wheels rotate, suspension bounces
- Blueprint UI showing exposed parameters: Speed, TurnAngle, DoorOpen
- Drone flying: propellers spinning, smooth hover
- Tank: turret aiming at target, barrel elevating
- Validation report visible on screen (score 87/100, all checks green)

### Voiceover Script
"Inside Unreal Engine: the car drives, the drone flies, and the tank aims - all from a single RigForge AI processing run. No manual cleanup. No technical artist required. AI-generated 3D assets, made interactive."

### Closing Text
"RigForge AI - Open source. Built for Unreal creators."
"github.com/arielshad/rigforge-ai"

---

## Production Notes

### Screen Recording Setup
- Resolution: 1920x1080 minimum, 4K preferred
- Frame rate: 60fps for smooth animation playback
- Software: OBS Studio, Loom, or native macOS screen recording

### Voiceover
- Clear, professional tone
- Record in quiet environment
- Sync timing with visual transitions

### Music (optional)
- Subtle, non-distracting background music
- Royalty-free preferred (Epidemic Sound, Artlist, YouTube Audio Library)
- Fade out for voiceover sections

### Editing
- Hard cuts between segments (no slow dissolves)
- Text overlays: clean white on dark background
- Highlight key UI elements with subtle zoom or circle
- Keep total length under 2:05

---

## Alternative Short Version (60 seconds)

For social media / community sharing:

| Segment | Duration |
|---------|----------|
| Problem (show broken model) | 0:00 - 0:10 |
| Pipeline running (fast montage) | 0:10 - 0:25 |
| Before / After split | 0:25 - 0:45 |
| Unreal demo | 0:45 - 1:00 |

---

## Key Moments to Capture

1. The "aha" moment: wheels fused to body (0:05)
2. Agent names appearing on screen (0:20-0:40)
3. Side-by-side before/after split screen (0:45)
4. Wheels rotating correctly in Blender (0:50)
5. Turret rotating independently in Unreal (1:20)
6. Validation score: 87/100 all green (1:45)
7. Repository URL visible at end (1:58)

---

## Checklist Before Recording

- [ ] Sample AI-generated car model ready (looks impressive but is broken)
- [ ] RigForge AI pipeline working on that model
- [ ] Blender scene prepared for before/after split
- [ ] Unreal demo level ready with all 3 assets
- [ ] Blueprint UI visible and labeled
- [ ] Validation report visible and readable
- [ ] Screen at 1080p or 4K
- [ ] Microphone tested and clean
- [ ] No distracting desktop icons visible
- [ ] GitHub repo URL correct in final frame

---

*RigForge AI - Demo Script v1.0 - May 2026*
*Target submission: Epic MegaGrants Cycle 2 - June 29, 2026*
