# claude-mods

A Claude Code plugin marketplace that re-exposes mods kept in other people's monorepos.

`claude plugin marketplace add owner/repo` only reads `.claude-plugin/marketplace.json` at the
root of a repository. Anthropic's example mods live under `claude-code/mods/` in
[anthropics/claude-code-playground](https://github.com/anthropics/claude-code-playground), so
they cannot be added that way. This marketplace points at each of them with a `git-subdir`
source, which is what Claude Code provides for exactly this case.

## Install

```bash
claude plugin marketplace add ChristianLemer/claude-mods
claude plugin install blast-radius@claude-mods --scope user
claude plugin install replay-theater@claude-mods --scope user
```

The mods need Claude Code 2.1.287 or later.

## Contents

| Plugin | What it does | Upstream |
| --- | --- | --- |
| `blast-radius` | Holds a risky shell command, shows what it would change, asks Proceed or Cancel | `claude-code/mods/blast-radius` |
| `replay-theater` | Steps through the last turn's file edits one diff at a time (`/replay`) | `claude-code/mods/replay-theater` |

Each entry follows the upstream default branch. To freeze one, add `"sha"` (a full 40-character
commit) to its source. The upstream repository says: *shared as-is, not an official Anthropic
product; no support or maintenance is implied.*
