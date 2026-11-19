# FAQ

**Is the source code available?** No. The Gryvia Apple source code is private. This repository holds documentation, the website and the downloads.

**How do I try it?** The app runs without a key. For a free 30-day trial key, email sales@zyvor.dev. Download the notarized DMG from the [release page](https://github.com/zyvorai/gryvia-apple/releases/tag/v0.5.2). Licences are at https://zyvor.dev/buy; the terms are in [LICENSE](../LICENSE) and [COMMERCIAL-LICENSE.md](COMMERCIAL-LICENSE.md).

**What does it need?** macOS 15 or later on Apple silicon.

**Does it split one model across several Macs?** No. For that, look at exo or MLX distributed. Gryvia decides which whole job runs on which Mac and under whose quota.

**Is GPU utilisation per job?** No. It is the whole Mac's GPU load as macOS reports it, including other apps. Reservations are admission bookkeeping and energy figures are estimates.

**Can I use a Mac that someone is also working on?** Yes: set its policy to "only when I am away".

**What does it send where?** Agents poll your control plane outbound. Nothing is sent to Zyvor. Models are downloaded only from huggingface.co or hf.co, with a size cap and a recorded SHA-256.

**Do deployed models hold memory forever?** Only until you stop them. Idle eviction is opt-in; there is no autoscaler.

**Which Macs and runtimes?** Apple silicon on macOS 15 or later. llama.cpp (GGUF), MLX and Core ML wrappers ship in the app, and runtimes are enabled per Mac.

**How do I report a vulnerability?** security@zyvor.dev; see [SECURITY.md](../SECURITY.md).
