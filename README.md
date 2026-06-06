# opencode-landstrip

Landlock-based sandboxing for [opencode](https://opencode.ai/) using
[`landstrip`](https://github.com/jarkkojs/landstrip).

## Prerequisites

Install `landstrip` and make sure it is on the `PATH` used to launch opencode:

```bash
cargo install landstrip
```

`landstrip` supports Linux, macOS, and Windows. On other platforms this plugin
loads but leaves sandboxing disabled.

## Install

Add the plugin to `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": ["opencode-landstrip"]
}
```

## Configure

Create `.opencode/sandbox.json` in a project or
`~/.config/opencode/sandbox.json` globally. Project config takes precedence.

See [`sandbox.json`](./sandbox.json) for a starter config.

## Behavior

The plugin wraps opencode's AI `bash` tool in `landstrip`, routes proxy-aware
network traffic through an allowlist proxy, and blocks read/write tool access
outside configured filesystem allowlists.

opencode's current server plugin API does not expose Pi-style custom permission
dialogs or a way to rewrite manually typed shell-mode commands. Blocked access
fails with an error that points at the sandbox config files.

## Disable

Set `enabled` to `false` in `sandbox.json`, or pass plugin options:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": [["opencode-landstrip", { "enabled": false }]]
}
```

## License

`opencode-landstrip` is licensed under `MIT`. See [LICENSE](LICENSE) for more
information.
