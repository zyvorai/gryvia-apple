# User guide

## Fleet and owner policy

Each Mac reports its GPU model, core count and measured utilisation, memory, thermal state, owner presence and power. Each Mac has an owner policy: always, only when its owner is away, or paused. Battery, Low Power Mode and call guards apply. Work starts after the idle time you choose and yields the moment the owner returns, and a yielded job is requeued without using a retry. Drain stops new claims and keeps active jobs.

## Admission and quotas

Jobs are admitted against each Mac's unified-memory budget, with priorities, tenant quotas, GiB-hour budgets and fairness weights. Tenant tokens see and act only on their own jobs. Job selectors can avoid Macs or require a minimum number of GPU cores or GiB. Open a queued job to see why it is waiting.

## Models

Onboard a model from Hugging Face (huggingface.co or hf.co only, with a size cap and a recorded SHA-256), check that it fits before you download it (the fit figure is an estimate), then benchmark, evaluate or fine-tune it. Fine-tuning is MLX LoRA on a single Mac, and a sweep fans a grid of up to 12 fine-tunes out as ordinary queued jobs, ranked by validation loss.

## Serving

Deploy a model on one Mac or on several (one replica per Mac, up to 8). The gateway is OpenAI-style, supports streaming, sends each request to the replica with the fewest in flight, and tries one other replica before returning 502; a stream fails over only before its first byte. There is no autoscaler: a lost replica is not replaced for you.

Deployments hold their memory reservation until stopped. **Idle deployments** on the Overview lists those with no gateway traffic in a window you choose, and stops them by hand; automatic eviction is opt-in and off by default. An evicted model returns to ready and is not redeployed for you.

## Provenance

Agents sign a statement for each finished job binding the job, its spec hash and its result. Model artifacts carry SHA-256 hashes. This is fleet-internal provenance, not a global supply-chain guarantee.

## Assistants

The MCP server is read-only by default; write tools (submit, cancel, set a Mac's policy) exist only when it is started with write access, and they run with the role of the token you give it. Shortcuts actions cover fleet status, a demo job and pausing a Mac.

## Honest limits

One GPU per Mac; GPU utilisation is device-wide, not per job; reservations are bookkeeping, not isolation; energy is an estimate; runtimes are not sandboxed. See [SECURITY.md](../SECURITY.md).
