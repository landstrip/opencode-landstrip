# pi-landstrip

![pi-landstrip screenshot](screenshot.png)

Landlock-based sandboxing for [pi](https://pi.dev/) using
[`landstrip`](https://github.com/landstrip/landstrip).

## Install

```bash
pi install npm:pi-landstrip
```

This installs `pi-landstrip` and its `@landstrip/landstrip` dependency, which
includes platform-specific native binaries for Linux, macOS, and Windows.

On unsupported platforms the extension loads but leaves sandboxing disabled.

## Configure

Create `.pi/sandbox.json` in a project or `~/.pi/agent/sandbox.json` globally.
Project config takes precedence.

See [`sandbox.json`](./sandbox.json) for a starter config.

Use sandbox config to toggle sandboxing:

```json
{
  "enabled": false
}
```

Project config overrides global config.
The `/sandbox` UI updates the project config when present, otherwise the global config.

## Usage

Use `/sandbox` inside Pi to show the active config and toggle sandboxing.

## License

`pi-landstrip` is licensed under `MIT`. See [LICENSE](LICENSE) for more
information.

The bundled `@landstrip/landstrip` package is licensed under
`Apache-2.0 AND LGPL-2.1-or-later`.
