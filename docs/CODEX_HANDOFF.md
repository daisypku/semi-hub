# CODEX_HANDOFF.md — SuperNode Hub

Last updated: 2026-08-17
Owner / research framework: DaisyPKU
Public repo: `daisypku/semi-hub`

## 1. Goal

Build Semi Hub into a living AI Hardware research atlas that works at two levels at once:

- A university student with no industry background can establish a complete mental model quickly.
- An equity researcher can map technology transitions into value pools, public companies, evidence quality and follow-up questions.

SuperNode is the top-level system map. Existing CCL/PCB/packaging/optics work becomes a linked sub-map rather than a separate project.

## 2. Core architecture decision

Do NOT create a separate public `supernode-hub` repository.

Use:
- `semi-hub` = PUBLIC publication layer / research atlas.
- `semi-research-core` = PRIVATE research engine containing expert notes, unverified supply-chain claims, detailed BOM assumptions, scoring, value estimates and meeting questions.

Public output should demonstrate the framework and evidence. Private research should retain the information advantage and the reproducible research process.

## 3. Conceptual model

Mental hierarchy:
accelerator card → server / tray → Scale-up supernode → Scale-out cluster / AI factory.

Key distinction:
- Scale-up: tightly connects accelerators so they behave more like one logical computer.
- Scale-out: connects multiple nodes/supernodes into a larger cluster.

Global route framing:
1. NVIDIA proprietary stack — GPU + NVLink/NVSwitch + networking + CUDA.
2. AMD / open ecosystem — rack-scale systems + UALink / UEC / OCP.
3. China domestic compute — large Scale-up domains and system engineering, with Huawei SuperPoD as a key public anchor.

Do not oversimplify China as “low precision” and overseas as “high precision.” FP8/FP4 are global AI trends.

## 4. Version history

### v0.1
Created:
- SuperNode Hub public page.
- Three compute routes.
- Eight-layer chain: Compute, Memory, Scale-up, Scale-out, Switching, Optics, PCB/CCL, Power/Cooling, Software.
- Evidence tiers S1/S2/S3.
- Link to existing `diagram002.html`.

### v0.2
Added:
- Topology Lab concept and `topologies.json`.
- Company Passport concept and `companies.json`.
- Named topology anchors instead of generic “72/384/1024/8192”.
- Public/private separation strengthened.

Important deployment lesson:
At first the two JSON files were uploaded but `supernode/index.html` was not overwritten, so the public page stayed on v0.1. Future deployments must validate the HTML version and JSON fetches together.

### v0.3
Successfully deployed to `main`.
Added:
- Topology Lab.
- Company Passport.
- Value Map.
- `value_map.json`.
- Public structural intensity score (1–5), explicitly NOT BOM dollars / earnings growth / valuation.
- Elasticity classes:
  - linear expansion
  - generation upgrade
  - superlinear / scale elasticity
  - technology shift / substitution

### v0.4
Added:
- Value Map components now filter Company Passports directly.
- Explicit public `value_links` map each company to a component and a visible structural driver.
- Component, industry-layer, architecture-route and keyword filters work together.
- Architecture filters: NVIDIA / Open / China / Cross-architecture.
- The repository README now links directly to the public SuperNode page.

Usability revision kept within v0.4:
- Section 02 was rebuilt as an interactive industry-chain navigator that explains what each layer does, where it sits in the system and what to study next.
- Section 03 was rebuilt as a reader-oriented system comparison. It explicitly separates the Scale-up boundary, compute side, Scale-up fabric, connection medium, system support and external Scale-out network.
- The six topology anchors now include plain-language summaries and a comparison table instead of relying on abstract rack-box counts.
- Value Map now appears as Section 04 before Company Passport as Section 05, creating a forward reading path: choose a value component, understand the mechanism, then view matching companies.

Follow-up revision on 2026-08-17, still within v0.4:
- Section 02 now uses a master-detail layout: all eight industry-chain layers remain visible in a left column while the selected layer's explanation appears on the right.
- The NVL576 card separates NVIDIA-confirmed S1 architecture facts from a clearly labeled SemiAnalysis S2 public research observation.
- Publicly confirmed NVL576 anchors now include eight 72-GPU MGX NVL racks, a two-layer all-to-all NVLink topology, copper plus direct optical connections, and the functional GB200-based Polyphe prototype.
- Pluggable optics versus CPO, volume timing and final implementation remain explicitly unresolved; no fixed optics BOM is published.

Current public page title contains `SuperNode Hub v0.4`.

## 5. Named topology anchors

Use named systems/standards, not anonymous accelerator counts:
- NVIDIA NVL72
- AMD Helios 72
- Huawei Atlas 900 A3 — 384 NPU
- NVIDIA Rubin Ultra NVL576
- UALink 1.0 — up to 1,024 accelerators as a protocol envelope, NOT one fixed product
- Huawei Atlas 950 — up to 8,192 NPU

Exact detailed BOMs should remain private unless independently public and intentionally released.

## 6. Public Value Map methodology

The public page asks:
“As the Scale-up domain grows, where does system value accrue?”

Components include:
- AI accelerator
- HBM / memory
- Scale-up switch / fabric
- NIC / DPU / Scale-out network
- Copper / DAC
- AEC
- Pluggable / direct optics
- CPO / Optical I/O
- PCB / CCL / connectors
- Power delivery
- Liquid cooling
- Software / reliability

The 1–5 intensity score is only a structural research index.

Important research idea:
System value growth and per-accelerator value growth are different questions.

Examples:
- Accelerator count: generally linear system expansion.
- HBM: more generation/configuration driven than supernode-size driven.
- Scale-up switching: potentially superlinear due to fabric depth/radix/redundancy.
- Optics: potentially superlinear when Scale-up crosses racks.
- Copper: may lose share as distance/bandwidth pushes links toward AEC/optics/CPO.
- Liquid cooling: increasingly tied to rack power density and MW-scale deployment.
- Software/reliability: complexity rises nonlinearly with domain size; goodput matters more than peak FLOPS.

## 7. Company Passport rules

Public passport fields:
- ticker / company
- layer
- architecture/exposure label
- role
- public thesis
- tracking metrics
- evidence tier + source

Never label a company an NVIDIA/Huawei supplier without public evidence or explicit release approval.

Seed public names currently include global and China-listed examples across compute, switching/networking, optics, PCB and cooling.

Current interaction:
Value Map components filter Company Passports directly. The page order intentionally places Value Map before Company Passport so component clicks move forward rather than backward.

## 8. Private research model

Private repository should hold exact assumptions.

Recommended location:
`semi-research-core/supernode/models/value_model.template.csv`

Suggested private structure:
```
semi-research-core/
├── AGENTS.md
├── README_PRIVATE.md
├── docs/
│   └── CODEX_HANDOFF.md
└── supernode/
    ├── evidence/
    │   └── evidence_registry.csv
    ├── meetings/
    │   └── YYYY-MM-DD_topic.md
    ├── models/
    │   ├── value_model.template.csv
    │   ├── topology_assumptions.json
    │   └── company_scores.json
    ├── questions/
    │   └── meeting_questions.md
    └── release/
        └── public_release_checklist.md
```

Private model principle:
`Total system value = fixed system value + per-accelerator value × accelerator count + per-compute-cabinet value × compute cabinets + per-interconnect-cabinet value × interconnect cabinets`

Private model can contain:
- exact optics links / accelerator
- module counts and speeds
- copper/AEC/optics mix
- switch-to-compute cabinet ratio
- switch ASIC counts
- ASP assumptions
- supplier share assumptions
- cooling / power value per MW
- sensitivity and scenario cases

Do not copy these values into public JSON automatically.

## 9. Important expert-call information already discussed

An Aug-2026 China supernode expert call included claims about 384/640/1024 schemes, communication efficiency, optical-module ratios, deployment cadence and domestic switch chips.

Treat these as S2 until independently verified.

Specific caution:
- “384/640/1024” alone is not a standardized product name.
- The expert’s “H100 = 4P” may use sparse FP8 peak; comparison must normalize precision/sparsity.
- “Overseas pursues FP32/FP64” is misleading for LLM AI; NVIDIA and AMD also aggressively use FP8/FP4.
- A note saying “100 PFLOPS training needs hundreds of sets” appeared internally inconsistent and should not be published as fact without clarification.
- Communication-efficiency percentages are system/workload dependent, not fixed protocol constants.
- Optical module ratios are design-specific, not universal industry constants.

## 10. Next roadmap

After the v0.4 usability revision is stable, primary candidates include:
- More explicit topology diagrams for NVL72 / A3 384 / NVL576 / Atlas950.
- Source registry / citations view.
- Version changelog.
- Deep links from SuperNode components to existing/future CCL, optics, HBM, packaging, switching and cooling sub-hubs.

## 11. Definition of done for v0.4

- Static GitHub Pages remains functional.
- `diagram002.html` URL unchanged.
- Value Map component click/filter works on desktop and mobile.
- Company Passport filtering works with component + route filters together.
- No private S2/S3 exact BOM assumptions leaked into public code.
- All public facts have primary-source links where practical.
- JSON schema remains readable and maintainable.
- Version updated from v0.3 to v0.4.
- `docs/CODEX_HANDOFF.md` changelog updated.

