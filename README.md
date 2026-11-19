<div align="center">

<img src="site/img/apple-touch-icon.png" width="96" alt="Gryvia">

# Gryvia Apple

### Your Macs, scheduled.

**A multi-tenant control plane for Apple Silicon fleets.** Gryvia admits and places inference, fine-tuning and benchmark jobs against each Mac's unified-memory budget, with quotas, leases, provenance and a live view of every GPU.

[Download](https://github.com/zyvorai/gryvia-apple/releases/tag/v0.5.2) · [Website](https://zyvorai.github.io/gryvia-apple/) · [Getting started](docs/GETTING-STARTED.md) · [User guide](docs/USER-GUIDE.md) · [FAQ](docs/FAQ.md) · [Security](SECURITY.md) · [Changelog](CHANGELOG.md)

</div>

This repository holds the documentation, the website and the downloads for Gryvia Apple. **The Gryvia Apple source code is private.**

## What it is

- **Memory-aware admission:** jobs are placed against each Mac's unified-memory budget, with priorities, tenant quotas and fairness weights.
- **Live fleet view:** GPU cores lit by measured utilisation, thermal state, drain and resume, alerts.
- **Owner-aware Macs:** run only when idle, yield when the owner returns, respect battery, Low Power Mode and calls.
- **One endpoint:** an OpenAI-style gateway with streaming, replicas on several Macs and one failover before the first byte.
- **Signed provenance:** node-signed attestations and verified chains for model artifacts.
- **Model workbench:** onboard from Hugging Face with a size cap and SHA-256, benchmark, evaluate, fine-tune with MLX LoRA, sweep a grid.
- **MCP server and Shortcuts actions** (read-only by default).

## Download and trial

- **[Gryvia-0.5.2.dmg](https://github.com/zyvorai/gryvia-apple/releases/tag/v0.5.2)**: Developer ID signed and notarized.
- **Requirements:** macOS 15 or later, Apple silicon.
- **Free 30-day trial key: sales@zyvor.dev**
- **Licence:** https://zyvor.dev/buy
- Verify the download: `shasum -a 256 -c Gryvia-0.5.2.dmg.sha256` (the checksum file is attached to the release).

The licence text is in [LICENSE](LICENSE); see also [docs/COMMERCIAL-LICENSE.md](docs/COMMERCIAL-LICENSE.md).

## Honest limits

One GPU per Mac; GPU utilisation is device-wide, not per job; reservations are admission bookkeeping, not isolation; energy is an estimate; training is single-Mac LoRA; there is no sandbox around runtimes, so enrol only Macs you would let an admin run code on. Replicas across two physical Macs are not yet measured. See [SECURITY.md](SECURITY.md).

## Docs

[Getting started](docs/GETTING-STARTED.md) · [User guide](docs/USER-GUIDE.md) · [FAQ](docs/FAQ.md) · [Commercial licence](docs/COMMERCIAL-LICENSE.md) · [Security](SECURITY.md) · [Changelog](CHANGELOG.md)
