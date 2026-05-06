# RigForge AI

> Agentic Rigging and Animation Pipeline for AI-Generated Mechanical 3D Assets

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Epic MegaGrants 2026](https://img.shields.io/badge/Epic-MegaGrants%202026-blue)](https://www.unrealengine.com/megagrants)
[![Status: Pre-Alpha](https://img.shields.io/badge/Status-Pre--Alpha-orange)]()

---

## One-Line Pitch

**We are building an AI agent workflow that converts raw AI-generated 3D vehicles, drones, tanks, and mechanical assets into clean, named, rigged, animated, physics-ready Unreal Engine assets.**

---

## The Problem

AI 3D generation is improving fast, but generated models are usually not production-ready.

For static renders, they look impressive. For games and simulations, **they break.**

### Typical issues with AI-generated mechanical models

- Car wheels are fused into the body
- Drone propellers are not separated
- Tank tracks are decorative geometry, not functional components
- Mesh parts have random names like object_003
- Origins, pivots, scale, hierarchy, normals, and UVs are often wrong
- No rig, skeleton, animation layer, collision setup, or physics behavior
- Importing into Unreal Engine still requires manual cleanup by a technical artist

**The gap is not generating a 3D model. The gap is making the generated model usable inside a game engine.**

---

## The Solution

RigForge AI is a system of small, specialized AI agents that inspect, repair, segment, name, rig, animate, test, and export generated 3D mechanical assets into Unreal Engine.

Inspired by software-development agents, the system breaks asset preparation into dedicated stages.

---

## Agent Architecture

```
Input: AI-generated 3D model (OBJ / FBX / GLB / USD)
         |
[1] Asset Analysis Agent       -- Detects asset type: car, drone, tank, aircraft, robot
         |
[2] Component Segmentation     -- Splits: wheels, doors, body, turret, tracks, propellers
         |
[3] Semantic Naming Agent      -- Creates clean hierarchy and component labels
         |
[4] Pivot and Transform Agent  -- Fixes origins, axes, rotations, transforms, scale
         |
[5] Rigging Agent              -- Builds control rigs or skeleton structures
         |
[6] Physics Agent              -- Creates collision meshes, constraints, mass, movement
         |
[7] Animation Agent            -- Generates base clips: wheel spin, steering, propeller rotation
         |
[8] Unreal Export Agent        -- Exports FBX/glTF/USD, imports into UE, creates Blueprint
         |
[9] Validation Agent           -- Runs automated tests, produces readiness report
         |
Output: Production-ready Unreal Engine asset
```

---

## Supported Asset Families (MVP)

| Category | Examples |
|----------|----------|
| Wheeled Vehicles | Cars, trucks, jeeps, military vehicles |
| Flying Mechanical | Drones, helicopters, aircraft |
| Tracked and Turreted | Tanks, APCs, sci-fi mechs |

---

## What We Are Building

### Blender Add-on
- Model inspection and analysis
- Component segmentation and grouping
- Semantic naming and hierarchy creation
- Pivot correction and scale normalization
- Export pipeline integration

### Unreal Engine Plugin / Import Script
- Automated asset import
- Blueprint generation utility
- Collision mesh setup
- Test map creation

### Agent Orchestration Layer
- Coordinates all specialized agents
- Handles failures and retries
- Produces asset readiness reports

### Validation Suite
- Automated checklist: Do wheels rotate independently?
- Scale validation against Unreal Engine units
- Pivot correctness checks
- Hierarchy integrity verification

### Demo Unreal Project
- Working car, drone, and tank assets
- Physics-driven movement in real time
- Playable demo scene

---

## Why This Fits Epic MegaGrants

This project is framed as an open-source creator tool for Unreal Engine, not a private startup product.

- Helps Unreal developers use AI-generated assets in real projects
- Supports games, simulation, automotive, robotics, digital twins, and education
- Improves the asset pipeline around Unreal Engine
- Released as open-source Blender/Unreal workflow
- Creates reusable benchmark datasets and test scenes for the community
- Connects AI agent technology with real-time 3D production workflows

---

## Measurable Success Criteria

- Process 30 sample generated assets across 3 categories: cars, drones, tanks
- Achieve correct component separation on at least 70% of test assets
- Achieve correct pivot placement on at least 70% of detected moving parts
- Generate Unreal-importable assets with no manual hierarchy cleanup
- Produce at least 10 working Unreal demo assets
- Release open-source Blender add-on and Unreal integration scripts
- Publish documentation and demo project for the community

---

## Milestone Overview

| # | Milestone | Duration |
|---|-----------|----------|
| 1 | Research and Prototype | Months 1-2 |
| 2 | Segmentation and Naming | Months 3-4 |
| 3 | Rigging and Animation | Months 5-7 |
| 4 | Unreal Engine Integration | Months 8-9 |
| 5 | Open-Source Release | Month 10 |

Full details in [MILESTONES.md](./MILESTONES.md)

---

## Budget Summary

**Total Funding Request: $175,000**

| Category | Amount |
|----------|--------|
| Technical Development | $40,000 |
| Blender / Unreal Plugin Work | $15,000 |
| AI / Agent Pipeline and Evaluation | $10,000 |
| Demo Assets, QA, Documentation, Video | $10,000 |
| AI Infrastructure (Inference, Servers, Cloud) | $100,000 |
| **Total** | **$175,000** |

Full breakdown in [BUDGET.md](./BUDGET.md)

---

## First 90-Day Execution Plan

**Days 1-30:** Build sample dataset, define component taxonomy, prototype Blender analysis script, create first Unreal import test.

**Days 31-60:** Add segmentation logic, pivot detection and correction, wheel/propeller/turret movement tests, first validation report, first before/after demo.

**Days 61-90:** Add Unreal Blueprint automation, build demo map with assets in motion, package alpha release, record MegaGrants demo video, publish GitHub repo and docs.

---

## Repository Structure

```
rigforge-ai/
+-- README.md                  <- This file
+-- GRANT_APPLICATION.md       <- Full Epic MegaGrants application text
+-- HANDOFF.md                 <- Complete project handoff document
+-- MILESTONES.md              <- Detailed milestone breakdown
+-- BUDGET.md                  <- Full budget breakdown
+-- ARCHITECTURE.md            <- Technical architecture deep-dive
+-- DEMO_SCRIPT.md             <- Demo video script (2-minute structure)
+-- LICENSE                    <- MIT License
+-- agents/                    <- Agent implementations (coming)
+-- blender_addon/             <- Blender add-on source (coming)
+-- unreal_plugin/             <- Unreal Engine plugin (coming)
+-- validation/                <- Validation suite (coming)
+-- assets/                    <- Sample and benchmark assets (coming)
+-- docs/                      <- Documentation (coming)
```

---

## Epic MegaGrants Application

- **Cycle 2 Submission Window:** June 29 - September 4, 2026
- **Review Period:** September 5 - December 4, 2026
- **Notices:** December 7-11, 2026

Full application text: [GRANT_APPLICATION.md](./GRANT_APPLICATION.md)

---

## License

MIT License - see [LICENSE](./LICENSE)

---

*RigForge AI - From static generated mesh to interactive real-time asset.*
