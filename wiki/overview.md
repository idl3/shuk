---
title: Shuk Overview
summary: Claude Code plugin marketplace — git-based distribution for Diakon and Olam
updated: 2026-04-10
confidence: seed
sources:
  - ../README.md
  - ../.claude-plugin/marketplace.json
---

# Shuk

*The open market.*

Shuk is a Claude Code plugin marketplace by idl3. The name comes from the Hebrew *shuk* — an open-air market where vendors offer their wares and buyers browse freely. Shuk is where Claude Code plugins are discovered and distributed.

## How It Works

Shuk distributes plugins via git repos. A marketplace manifest (`.claude-plugin/marketplace.json`) declares available plugins with their source URLs, versions, descriptions, and metadata. Users add the marketplace and install plugins by name.

```bash
/plugin marketplace add idl3/shuk
/plugin install dk@shuk      # workspace orchestration
/plugin install olam@shuk    # world engine
```

## Available Plugins

| Plugin | Version | Description | Repository |
|--------|---------|-------------|------------|
| **dk** (Diakon) | 0.2.0 | Multi-project workspace orchestration — manage projects, git operations, encrypted secrets, and LLM wikis (Karpathy pattern) across a unified workspace | [idl3/diakon](https://github.com/idl3/diakon) |
| **olam** | 0.1.0 | Agentic thinking platform — spawn isolated development worlds with thought graph capture, multi-runtime stack support, and team-level intelligence via Pleri | [idl3/olam](https://github.com/idl3/olam) |

## Marketplace Manifest

The `marketplace.json` lives at `.claude-plugin/marketplace.json` and contains:

- **name** — marketplace identifier (`shuk`)
- **owner** — author name and GitHub URL
- **plugins[]** — array of plugin entries, each with:
  - `name` — short install name (e.g. `dk`, `olam`)
  - `source.url` — git SSH URL for cloning
  - `version` — semver
  - `description` — one-line summary
  - `author`, `homepage`, `repository` — metadata
  - `license` — licensing terms
  - `keywords` — discoverability tags

## Architecture

Shuk is minimal by design. No registry server, no package manager, no build pipeline. Distribution is git clone. The marketplace manifest is the only required file. Plugins are self-contained repos with their own `.claude-plugin/plugin.json`.

## License

CC BY-NC 4.0 — free to use and adapt, not for commercial use.
