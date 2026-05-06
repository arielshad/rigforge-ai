# RigForge AI - Full Budget Breakdown

**Total Funding Request: $175,000**
**Grant Program:** Epic MegaGrants Cycle 2, 2026
**Project Duration:** 10 months

---

## Budget Summary

| Category | Amount | % of Total |
|----------|--------|-----------|
| Technical Development | $40,000 | 23% |
| Blender / Unreal Plugin Work | $15,000 | 9% |
| AI / Agent Pipeline and Evaluation | $10,000 | 6% |
| Demo Assets, QA, Documentation, Video | $10,000 | 6% |
| AI Infrastructure (Inference, Servers, Cloud) | $100,000 | 57% |
| **Total** | **$175,000** | **100%** |

---

## Category 1: Technical Development - $40,000

### What This Covers
Core engineering work across the entire 10-month project.

| Sub-Category | Amount | Notes |
|-------------|--------|-------|
| Agent architecture and orchestration framework | $12,000 | Building the pipeline that coordinates all 9 agents |
| Mesh analysis and segmentation algorithms | $10,000 | Geometry processing, cluster detection, symmetry analysis |
| Naming, hierarchy, and pivot correction systems | $8,000 | Semantic naming logic, parent-child hierarchy, pivot placement |
| Testing, debugging, and QA infrastructure | $6,000 | Test suites, CI/CD, benchmark evaluation |
| Integration and API work | $4,000 | Connecting Blender and Unreal Engine components |
| **Subtotal** | **$40,000** | |

### Assumptions
- Solo developer or small team (1-2 engineers)
- Approximately 400-500 hours of engineering time at $80-100/hr
- Covers Months 1-9 of the project

---

## Category 2: Blender / Unreal Plugin Work - $15,000

### What This Covers
Specialized add-on and plugin engineering for both tools.

| Sub-Category | Amount | Notes |
|-------------|--------|-------|
| Blender add-on development (Python) | $8,000 | Full add-on with UI, mesh operations, export pipeline |
| Unreal Engine plugin / import scripts | $5,000 | Python scripting, Blueprint utilities, automation |
| Cross-platform testing and compatibility | $2,000 | Windows/Mac, Blender 4.x versions, UE5.x versions |
| **Subtotal** | **$15,000** | |

### Assumptions
- Blender add-on: ~80 hours at $100/hr
- Unreal scripts: ~50 hours at $100/hr
- Testing and compatibility: ~20 hours

---

## Category 3: AI / Agent Pipeline and Evaluation - $10,000

### What This Covers
AI/ML work specific to the agent reasoning layer.

| Sub-Category | Amount | Notes |
|-------------|--------|-------|
| Prompt engineering and agent design | $3,000 | Designing agent instructions, chain-of-thought patterns |
| Evaluation framework and benchmarks | $3,000 | Building automated evaluation against known-good outputs |
| Fine-tuning or adapter training (if needed) | $2,000 | Optional: small adapter for mesh classification |
| Agent integration testing | $2,000 | Testing full pipeline end-to-end with real models |
| **Subtotal** | **$10,000** | |

---

## Category 4: Demo Assets, QA, Documentation, Video - $10,000

### What This Covers
Everything needed to demonstrate the project and ship to the community.

| Sub-Category | Amount | Notes |
|-------------|--------|-------|
| Sample AI-generated model sourcing/licensing | $2,000 | Acquiring or generating 30+ test models |
| Demo Unreal Engine project (3 playable scenes) | $2,000 | Asset assembly, Blueprint setup, level design |
| Documentation writing | $2,000 | README, guides, API docs, tutorials (~40 hours) |
| Demo video production (2-minute grant video) | $2,000 | Screen recording, editing, narration |
| Tutorial video production (3 x 5-minute videos) | $2,000 | One per asset type: car, drone, tank |
| **Subtotal** | **$10,000** | |

---

## Category 5: AI Infrastructure - $100,000

This is the largest and most critical budget category. Running AI agents on 3D geometry at scale requires significant compute resources that are not sustainable without grant support.

### What This Covers

| Sub-Category | Amount | Notes |
|-------------|--------|-------|
| LLM/VLM inference costs | $35,000 | Vision-language models for mesh understanding and component classification |
| GPU compute (training/fine-tuning) | $25,000 | Mesh analysis, segmentation model training, evaluation runs |
| Cloud infrastructure (storage, networking) | $15,000 | Benchmark datasets, model checkpoints, CI/CD |
| API costs (commercial AI services) | $15,000 | OpenAI/Anthropic/Google API calls during prototyping |
| Monitoring, logging, and ops | $5,000 | Infrastructure management tools |
| Buffer / contingency | $5,000 | For unexpected compute spikes or API cost increases |
| **Subtotal** | **$100,000** | |

### Detailed Justification

#### LLM/VLM Inference ($35,000)
The core innovation of RigForge AI is using vision-language models to "understand" 3D assets. Each model processed requires:
- Multiple agent calls to analyze geometry screenshots and point clouds
- Classification calls to identify component types
- Reasoning calls to determine pivot placement and hierarchy

Estimated: 30 test assets x 50 agent calls per asset x $2 per complex call = $3,000 for initial evaluation. At scale for 300+ assets and iterative development cycles over 10 months: $35,000.

#### GPU Compute ($25,000)
- Mesh segmentation model training: ~$5,000 (GPU hours on cloud)
- Repeated training runs for iteration: ~$10,000
- Evaluation runs against benchmark dataset: ~$5,000
- Real-time inference testing: ~$5,000

#### Cloud Storage and Networking ($15,000)
- Raw AI-generated model dataset: ~500GB
- Processed model dataset: ~500GB
- Model checkpoints and weights: ~200GB
- Transfer costs, CDN for documentation: ~$3,000/month x 10 months

#### Commercial API Costs ($15,000)
During prototyping, we will use commercial APIs (OpenAI GPT-4V, Anthropic Claude, Google Gemini) to test agent approaches before committing to open models. This allows faster iteration.

### Why $100K is Justified
- This is not overhead; it is the core compute that powers the agent pipeline
- Running 300+ assets through 9-agent pipeline = significant inference cost
- Training even lightweight segmentation models requires GPU compute
- The infrastructure investment creates reusable benchmark datasets for the community
- Without this budget, the project would be limited to toy-scale demos

---

## Budget by Milestone

| Milestone | Duration | Estimated Spend |
|-----------|----------|----------------|
| M1: Research and Prototype | Months 1-2 | $20,000 |
| M2: Segmentation and Naming | Months 3-4 | $35,000 |
| M3: Rigging and Animation | Months 5-7 | $50,000 |
| M4: Unreal Integration | Months 8-9 | $45,000 |
| M5: Open-Source Release | Month 10 | $25,000 |
| **Total** | **10 months** | **$175,000** |

Note: AI infrastructure costs (Category 5) are distributed across all milestones, with heavier spending in M2-M4 during active training and evaluation.

---

## Notes on Budget Flexibility

The base project (Blender add-on + Unreal integration + validation) can be delivered for $75,000. The additional $100,000 for AI infrastructure enables:
- Using state-of-the-art VLMs instead of simple heuristics
- Training custom segmentation models for better accuracy
- Processing 300+ assets instead of 30 for the evaluation suite
- Building community benchmark datasets at scale

If awarded less than the full $175,000, the project will proceed with the available budget, scaling back the AI training and evaluation scope accordingly.

---

*RigForge AI - Budget v1.0 - May 2026*
*Epic MegaGrants Cycle 2 Application*
