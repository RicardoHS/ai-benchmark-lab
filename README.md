# Homelab AI Benchmark Lab

Public, reproducible evidence from local AI-model evaluations on NVIDIA DGX
Spark hardware.

**Current status: preliminary.** The repository publishes individual observed
runs, including failures, but does not claim a final model ranking. A final
comparison requires frozen protocols, complete public suites and at least three
independent repetitions of each stochastic profile.

## Live results

- [Interactive benchmark index](https://ricardohs.github.io/ai-benchmarks/)
- [Machine-readable preliminary dataset](data/preliminary-results.json)
- [Creative benchmark prompt](methodology/creative-benchmark-report-v1.0.0.md)
- [Measurement and publication protocol](methodology/protocol.md)

## What is currently measured

| Track | Current evidence | Final status |
| --- | --- | --- |
| Creative benchmark report | Eight comparable first runs | Repetitions and fully verified deliveries pending |
| NP Frontier | MaxCut and Max-3SAT infrastructure smokes | Frozen multi-size suites pending |
| ARC-AGI-2 | Two exact attempts on one public training task | Complete evaluation pending |
| ARC-AGI-3 | Adapter validation only | Model scorecard pending |
| SWE-bench Verified | Upstream revision pinned privately | Runs pending |
| Terminal-Bench 2 | Upstream revision pinned privately | Runs pending |
| LiveCodeBench | Upstream revision pinned privately | Runs pending |
| BigCodeBench Hard | Upstream revision pinned privately | Runs pending |

## Interpretation rules

- A failed build or timeout is a benchmark result and is not repaired after the
  agent submits it.
- One creative run produces one delivery. The model does not generate several
  sites from which a preferred result is selected.
- Active decode throughput is not the same measurement as aggregate concurrent
  throughput or end-to-end agent speed.
- DGX Spark uses unified memory. Tables therefore say host/unified memory and do
  not mislabel it as conventional discrete VRAM.
- Third-party measurements are references, not local results, until reproduced.
- Smoke results verify infrastructure and are never presented as official
  benchmark scores.

## Privacy boundary

This public repository contains reviewed aggregate facts only. Internal
hostnames and addresses, credentials, raw agent sessions, private-repository
prompts, operational logs and unredacted node snapshots remain in the private
homelab repository.
