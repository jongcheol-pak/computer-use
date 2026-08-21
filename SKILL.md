---
name: maid-computer-use
description: >-
  Use Maid's computer-use CLI to inspect and operate local Windows desktop app
  windows through accessibility trees, screenshots, and safe UI actions. Use for
  desktop app interaction: list apps/windows, get app state, read visible UI,
  click controls, type, press keys, scroll, drag, set values, or perform
  accessibility actions. Also use for browser windows, webviews, Maid app UI, or
  other desktop UI. Triggers include "computer use", "maid computer", "read
  Notepad", "read Slack", "control/click/read in a desktop app", and "get app
  state".
version: 1.0.1
---

# Computer Use (Windows)

This file is a discovery stub, not the usage guide. The full, version-matched computer-use
reference is served by the `maid` binary itself — kept out of this file on purpose so it can
never drift from the binary that will actually run your commands.

Engage Maid's computer-use surface whenever you must inspect or operate a local desktop app
window — reading its accessibility tree, taking screenshots, or performing safe UI actions
(click controls, type, press keys, scroll, drag, set values). It also covers browser
windows, webviews, and Maid's own UI. Triggers include "computer use", "maid computer",
"read Notepad", "read Slack", "control/click/read in a desktop app", and "get app state".

This provider is **Windows-only**. It talks to UI Automation and Win32 directly — there is
no sidecar process and no PowerShell dependency.

## Resolve the CLI for this session

Choose the executable once and reuse it for every later command:

- If the `MAID_CLI_COMMAND` environment variable is set, use its value.
- Otherwise, use the `maid.exe` that is already on `PATH`.
- Otherwise, use the full path of the installed binary.

Below, `MAID` is a placeholder for the executable you resolved. Substitute it before
running anything; do not create a shell variable or run `MAID` literally. This works the
same way in PowerShell, cmd.exe, and POSIX shells.

If the selected executable cannot run, report its exact error and stop. Do not fall through
to another executable, which could silently target a different Maid build.

## Load the full guide before running Maid commands

```text
MAID skills get maid-computer-use
```

That prints the complete, version-matched guide for the exact binary that will handle your
next commands — listing apps/windows, reading UI, and driving clicks, typing, and other
accessibility actions. Read it first, then run the specific command you need.

Don't guess subcommands or flags from memory or from a cached copy of this stub. They may
change between Maid releases, and this file deliberately does not list them. Prefer
`--json` for agent-driven calls; **every response is JSON, including errors**.

## Orientation commands

These three are stable and safe to run before you have read the guide:

```text
MAID computer capabilities --json
MAID computer list-apps --json
MAID computer list-windows --app <name> --json
```

Beyond these, read the guide rather than guessing a command surface.

## Relationship to Orca's `computer-use`

This skill is deliberately named `maid-computer-use` so it can be installed alongside
Orca's `computer-use` without either one overwriting the other — both live under
`~/.agents/skills/`. If both are present, use the one that matches the app you intend to
drive: `maid computer ...` here, `orca computer ...` there.
