# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **Claude Code plugin marketplace index only**. It contains no plugin code — no agents, commands, or hooks. Its entire purpose is to publish [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json), which points Claude Code at the external repos where each plugin actually lives.

The single source of truth is [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json). Each entry names a plugin and a `source` (a GitHub `repo`) that hosts the plugin's implementation. Editing this file is how plugins are added, removed, renamed, or repointed. Keep [README.md](README.md)'s Plugins table in sync with it.

Plugin implementations are **not** in this repo. For example, `chrismou-project-manager` lives at `chrismou/claude-project-manager-workflow`. To change agent/command behavior, work in that repo, not here.

### History note

Plugin code used to live in this repo under `project-manager/`. It was split out into its own repo in commit `c2f7816` ("Convert to marketplace-only"). Git history before that commit contains the old in-repo agents and commands — useful for archaeology, but the working tree is intentionally marketplace-only now.

## Validation

There is no build or test suite. The only meaningful check is that the JSON is valid:

```bash
python3 -c "import json; json.load(open('.claude-plugin/marketplace.json')); print('OK')"
```

## Conventions

- Plugin `name` in `marketplace.json` is the identifier users install with (`claude plugin install <name>@chrismou-claude-plugins`). Renaming it is a breaking change for existing users.
- The `source.repo` must be a real, public GitHub repo containing a valid plugin (its own `.claude-plugin/plugin.json`). This repo does not vendor or mirror that content.
- Plugins that ship commands (ie, project manager) are generally prefixed `chrismou-` as it helps with finding them in the CLI. One time installation pligins, ie Claude hooks, do not require this prefix.
