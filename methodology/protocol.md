# Measurement and publication protocol

## Result identity

A row represents one exact combination of:

- checkpoint and immutable revision;
- quantization and KV-cache precision;
- inference runtime, container digest and local patches;
- hardware topology and tensor/pipeline parallelism;
- context limit, concurrency and cache state;
- sampling, reasoning mode, reasoning parser and tool parser;
- agent implementation, tool grants and network policy;
- workload revision, time budget and output-token budget.

Changing any of those creates a new profile rather than silently updating an
existing row.

## Repetition policy

One run is publishable as preliminary evidence. Final stochastic comparisons
require at least three independent runs under the same frozen profile; ten or
more are preferred when cost permits. Published aggregates include sample
count, mean, standard deviation, median and range. A timeout remains in the
sample instead of being discarded.

The creative track still produces only one delivery *per run*. Repetition is
used to estimate model/run variance, never to select the prettiest website and
hide the others.

## Timing and throughput

The following measurements remain separate:

- agent wall time;
- end-to-end wall time;
- verification wall time;
- model cold-load and warm-up time;
- time to first token/content/tool/browser action;
- active prefill and decode throughput;
- aggregate throughput at concurrency 1, 2 and 4;
- inter-token latency.

Server telemetry sampled during an agent run is labelled as such and cannot be
substituted for a controlled throughput benchmark.

## Memory and energy

DGX Spark exposes 128 GiB of unified memory. Each final run captures both nodes
simultaneously and records idle-after-load, peak used, minimum free, process or
cgroup peak, swap, KV reservation, checkpoint/transformed storage, power and
energy where supported. Post-run host snapshots are retained as preliminary
evidence but are not compared as isolated model peaks.

## Creative benchmark report

Every agent receives the same versioned prompt and a hashed read-only brief. It
works in a fresh directory, chooses its own design and decides when it is ready.
The objective verifier then performs a clean Node build and exercises the site
at phone, tablet, desktop and wide viewports with external runtime requests
blocked. Browser checks cover console errors, overflow, links, keyboard use,
reduced motion, WebGL and a forced non-WebGL fallback.

The published outcome is objective (`passed`, `passed-with-notes`, `failed` or
`incomplete`). No subjective numerical design rubric is used. Readers can judge
creative quality from the immutable delivery, screenshots and audit evidence.

## Public-suite boundary

ARC training smokes, tiny optimization instances and harness unit tests are
labelled as infrastructure validation. They are not transformed into official
scores. A public score is emitted only after the frozen evaluation split and
official scorer complete successfully.

## Publication boundary

Only reviewed summaries enter this repository. Raw model responses, complete
agent traces, private prompts, secrets, network identifiers and operational logs
are denied. Published data is immutable by run ID; a rerun receives a new ID.
