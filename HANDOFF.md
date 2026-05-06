# RigForge AI - Complete Project Handoff

**Date:** May 6, 2026
**Project:** RigForge AI
**Status:** Pre-Application / Pre-Development
**Next Action:** Submit to Epic MegaGrants Cycle 2 (opens June 29, 2026)

---

## Session Summary

This document captures the complete context, decisions, strategy, and materials from the initial project development session. Anyone picking this up should be able to continue without missing any context.

---

## What Was Created in This Session

### Strategic Framing
- Identified the correct Epic MegaGrants angle: not AI 3D model generation (too crowded), but the missing bridge between AI-generated 3D assets and production-ready Unreal Engine animation/simulation
- Framed as an open-source creator tool for Unreal Engine, which directly matches Epic's stated grant priorities
- Scoped tightly to mechanical objects (vehicles, drones, tanks) where movement rules are functional and testable, not artistic

### Project Name Decision
- Selected: **RigForge AI**
- Subtitle: Agentic pipeline for turning AI-generated mechanical 3D models into animation-ready Unreal Engine assets
- Runner-up options considered: MechRig Agents, MotionSmith, AssetOps AI, ForgeRig for Unreal

### Grant Strategy
- Confirmed fit with Epic MegaGrants criteria: open-source tools, Unreal pipeline improvement, smaller teams/innovators
- Funding request set at **$175,000** (original $75K + $100K added for AI infrastructure: inference, servers, cloud)
- Target: Cycle 2 submission window June 29 - September 4, 2026

### Materials Prepared
All documents in this repository constitute the complete grant preparation package.

---

## The Grant Concept

### Best MegaGrants Angle
Not "AI 3D model generation" - that space is crowded and Epic knows it.
The angle is: **the missing bridge between AI-generated 3D assets and production-ready Unreal Engine animation/simulation.**

### Why This Works
- Epic says MegaGrants are for projects pushing real-time 3D development forward, especially smaller teams and innovators using Epic technology
- Epic explicitly includes open-source tools or projects that advance the 3D community
- AI-generated models look great but are not interactive - this is the bottleneck
- The fix requires technical-art work that is repetitive, structured, and automatable
- Agentic workflows are proven in software development - applying them to 3D prep is the novel insight

---

## The Problem Statement (Full Version)

AI 3D generation is improving fast, but generated models are usually not production-ready.

For static renders, they look impressive. For games and simulations, they break.

Typical issues:
- Car wheels are fused into the body
- Drone propellers are not separated
- Tank tracks are decorative geometry, not functional components
- Mesh parts have random names like object_003
- Origins, pivots, scale, hierarchy, normals, and UVs are often wrong
- No rig, skeleton, animation layer, collision setup, or physics behavior
- Importing the model into Unreal Engine still requires manual cleanup by a technical artist

The gap is not "generate a 3D model." The gap is "make the generated model usable inside a game engine."

---

## The Technical Architecture

### 9-Agent Pipeline
1. Asset Analysis Agent - Detects asset type (car, drone, tank, aircraft, robot)
2. Component Segmentation Agent - Splits model into meaningful parts
3. Semantic Naming Agent - Creates clean hierarchy and component labels
4. Pivot and Transform Agent - Places correct origins and rotation axes
5. Rigging Agent - Builds control rigs or skeleton structures
6. Physics and Collision Agent - Creates collision meshes, constraints, mass, movement behavior
7. Animation Agent - Generates base animation clips
8. Unreal Export Agent - Exports to FBX/glTF/USD, imports into UE, creates Blueprints
9. Validation Agent - Runs automated validation and produces readiness report

### Technology Stack (Planned)
- Blender Python API for mesh manipulation
- Vision-Language Models (VLMs) for asset type detection and component understanding
- Open3D or trimesh for geometry analysis
- Unreal Engine Python scripting / Blueprint automation
- Agent orchestration framework (LangGraph or similar)

---

## Budget Breakdown

**Total: $175,000**

| Category | Amount | Notes |
|----------|--------|-------|
| Technical Development | $40,000 | Core agent and pipeline development |
| Blender / Unreal Plugin Work | $15,000 | Add-on and plugin engineering |
| AI / Agent Pipeline and Evaluation | $10,000 | Agent framework, prompt engineering, evals |
| Demo Assets, QA, Documentation, Video | $10,000 | Content for submission and community |
| AI Infrastructure | $100,000 | Inference, servers, cloud (see note) |
| **Total** | **$175,000** | |

### AI Infrastructure Note
$100,000 covers:
- LLM/VLM inference for agent reasoning (mesh understanding, component classification)
- GPU compute for mesh analysis and segmentation model training
- Cloud storage for benchmark datasets and model checkpoints
- CI/CD infrastructure for automated validation runs
- API costs for commercial AI services during prototyping phase
- This is essential because running AI agents on 3D geometry at scale is compute-intensive

---

## Milestones

| # | Title | Duration | Key Deliverables |
|---|-------|----------|-----------------|
| 1 | Research and Prototype | Months 1-2 | Asset taxonomy, sample dataset, first Blender pipeline, basic agent orchestration |
| 2 | Segmentation and Naming | Months 3-4 | Component grouping, semantic naming, hierarchy cleanup, pivot placement, first validation report |
| 3 | Rigging and Animation | Months 5-7 | Wheel/propeller/turret animation, suspension, export-ready rig structures |
| 4 | Unreal Engine Integration | Months 8-9 | Import automation, Blueprint generation, collision, test maps, playable demo |
| 5 | Open-Source Release | Month 10 | GitHub repo, docs, example assets, demo videos, tutorials, community feedback |

---

## Framing Rules (Maintain These)

### Use These Phrases
- AI-to-Unreal asset pipeline
- Animation-readiness layer for generated 3D models
- Agentic technical-art automation
- Open-source tool for the Unreal creator community
- From static generated mesh to interactive real-time asset
- Mechanical asset rigging for vehicles, drones, and simulation objects

### Avoid These Framings
- We are building another AI 3D generator
- We replace artists
- Fully autonomous universal rigging for every model
- We need money to start exploring
- We will handle all asset types

### Make It Sound Like
- We identified a concrete bottleneck
- We have a narrow first scope (vehicles, drones, tanks only)
- We are building tooling that benefits Unreal creators
- The output is demonstrable and measurable
- This is open-source for the community

---

## What Still Needs to Be Done

### Before June 29, 2026 (Submission Opens)

**Critical**
- [ ] Build working prototype (even basic Blender script that separates wheels)
- [ ] Record 2-minute demo video following DEMO_SCRIPT.md
- [ ] Create Unreal demo scene with at least one vehicle moving
- [ ] Set up Epic Games account if not already done

**Important**
- [ ] Create GitHub Pages or project landing page (optional but helpful)
- [ ] Write project blog post or devlog to establish presence
- [ ] Collect any community feedback or interest to demonstrate demand

**Nice to Have**
- [ ] Add GitHub Topics: unreal-engine, blender, ai, animation, rigging, open-source, game-development
- [ ] Add repository social preview image
- [ ] Create a brief architecture diagram (can be hand-drawn)
- [ ] Record a longer technical overview video

### For the Application Form (June 29 - September 4, 2026)
- Full application text is in GRANT_APPLICATION.md
- Use the exact framing from that document
- The form will require an Epic Games account login
- Have the demo video URL ready (YouTube or Vimeo)
- Have the GitHub repo URL ready: https://github.com/arielshad/rigforge-ai

---

## Key Decisions Made

| Decision | Choice | Reasoning |
|----------|--------|-----------|
| Grant angle | Asset prep pipeline, not generation | Less crowded, clearer problem |
| Project name | RigForge AI | Clear, production-oriented, memorable |
| First scope | Cars, drones, tanks only | Narrow scope is more credible |
| Open-source commitment | Yes, MIT license | Better fit with MegaGrants criteria |
| Funding ask | $175,000 | $75K base + $100K AI infrastructure |
| License | MIT | Maximum community use |

---

## Repository Files

| File | Purpose |
|------|---------|
| README.md | Main project overview with badges, architecture, milestones |
| GRANT_APPLICATION.md | Complete application text ready to paste |
| HANDOFF.md | This file - complete session context |
| MILESTONES.md | Detailed milestone breakdown with deliverables |
| BUDGET.md | Full budget breakdown with justifications |
| ARCHITECTURE.md | Technical architecture deep-dive |
| DEMO_SCRIPT.md | 2-minute demo video script for application |

---

## Timeline

| Date | Event |
|------|-------|
| May 6, 2026 | Project concept and strategy session; all documents created |
| June 29, 2026 | Epic MegaGrants Cycle 2 submission window opens |
| September 4, 2026 | Submission window closes (11:59 PM ET) |
| September 5 - December 4, 2026 | Review period |
| December 7-11, 2026 | Notices sent |

---

## Contact

**Project Owner:** Ariel Shadkhan
**GitHub:** https://github.com/arielshad
**Repository:** https://github.com/arielshad/rigforge-ai

---

*This handoff document was generated on May 6, 2026 and captures the full project context from the initial strategy and planning session.*
