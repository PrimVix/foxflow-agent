# FoxFlow Agent

The local helper for [FoxFlow](https://autovideo-3bi.pages.dev). It runs **only on your
computer** and lets the FoxFlow website drive image generation, voiceover and video
assembly on your behalf.

> **Why a local agent?** Generation happens inside your own browser session — under your
> own login, with your own cookies. A website alone can't do that securely (browser
> same-origin rules). So FoxFlow ships a small agent that runs locally and talks to the
> site over `127.0.0.1` (your machine only). Nothing is sent to us.

## Download

Grab the latest build from **[Releases](../../releases)** → `FoxFlowAgent.zip`.

1. Unzip anywhere.
2. Run `FoxFlowAgent.exe` once. It starts in the background and a small console window
   shows its status.
3. Open the FoxFlow website — it connects to the agent automatically.

Windows 10/11. No Python install needed — everything is bundled.

## Is it safe? What it does and doesn't

FoxFlow Agent is designed to be **transparent and minimal**:

- ✅ **Listens only on `127.0.0.1:8765`** (loopback). It is **not** reachable from the
  internet or other machines — only the page open on your own computer can talk to it.
- ✅ **Origin allowlist + pairing PIN.** Only the FoxFlow site can send it commands, and
  only after you pair it with a one-time PIN shown in its console. A random website
  cannot hijack it.
- ✅ **Your account token is encrypted at rest** with Windows DPAPI — tied to your
  Windows user, useless if copied to another machine.
- ✅ **No telemetry, no analytics, no data leaves your machine** except the requests you
  explicitly trigger (image/voice generation through your own logged-in services).
- ✅ **Open release, reproducible behaviour.** The console window shows exactly what it's
  doing. You can inspect every network call with any local proxy/devtools.
- ❌ It does **not** read files outside its working folder, install anything system-wide,
  or run at startup unless you set that up yourself.

## How it works (high level)

```
FoxFlow website  ──https──►  FoxFlow Agent (127.0.0.1:8765)  ──►  your browser session
   (you, logged in)              (this program, local only)         (your own login)
```

The agent never holds your passwords. It works through a browser session you control.

## Support

Questions or issues → [open an issue](../../issues) or contact support on the website.

## License

The compiled agent is distributed for use with FoxFlow. © FoxFlow. All rights reserved.
