# Getting started

Gryvia schedules jobs across your Macs and serves models from them behind one OpenAI-style endpoint.

**You need:** an Apple silicon Mac on macOS 15 or later. A second Mac is optional.

## 1. Download and verify

Download `Gryvia-0.5.2.dmg` and `Gryvia-0.5.2.dmg.sha256` from the [release page](https://github.com/zyvorai/gryvia-apple/releases/tag/v0.5.2). The DMG is Developer ID signed and notarized.

```bash
shasum -a 256 -c Gryvia-0.5.2.dmg.sha256
```

The app runs without a key. For a free 30-day trial key, email sales@zyvor.dev. The trial is soft: nothing is disabled and no data is lost when it ends. Licences are at https://zyvor.dev/buy.

## 2. Install and open

Open the DMG and drag **Gryvia.app** to Applications. The first launch shows a short Welcome; reopen it from **Help**. Paste an admin token once; it goes to your login Keychain. Press **Run demo job** to see admission, a lease and a result.

**Command-K** opens a command palette (jump to a pane, run the demo job, submit), **Command-1 to Command-0** switch panes, and clicking an underlined term such as *reserved* explains it. Open a queued job to see why it is waiting. Reservations are bookkeeping, not a GPU meter.

## 3. Add a Mac

Use **Add a Mac** in the app or the web dashboard to create a single-use join code (valid 15 minutes) and enter it on the new Mac. No config edit or restart is needed. A Mac's token can be revoked. A control plane that other Macs reach must use HTTPS; plain HTTP is accepted only for loopback.

## 4. Call a model

Once a model is deployed, call it with a tenant token:

```bash
curl -s http://127.0.0.1:8443/v1/chat/completions \
  -H "Authorization: Bearer $GRYVIA_TENANT_TOKEN" -H 'Content-Type: application/json' \
  -d '{"model":"my-llama","messages":[{"role":"user","content":"Say hi"}]}'
```

Add `"stream": true` for server-sent events. Model servers listen on the worker's loopback only, and your platform token never reaches them.

## When something is wrong

| Symptom | Check |
|---|---|
| Deploy stays queued | Is the Mac online, not drained, with enough free GiB and the model on it? |
| Request returns 503 | The model is not deployed, was evicted, or its Mac is offline. |
| Request returns 502 | The replica failed; with replicas the gateway already tried one other. |
| Gatekeeper blocks the app | Verify the checksum; the 0.5.2 DMG is notarized, so a block usually means a damaged download. |

See the [User guide](USER-GUIDE.md) and the [FAQ](FAQ.md).
