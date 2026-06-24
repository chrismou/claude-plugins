# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.4] - 2026-06-24

### Added

- CI `version-bump` workflow — every PR into `main` must raise `plugin.json` (and keep `marketplace.json` in sync) to a version strictly greater than the base branch, or the check fails and the merge is blocked.

## [0.0.3] - 2026-06-24

### Added

- `project-manager-test` slash command — an isolated copy of `project-manager` that trials the architect clarifying-questions flow without affecting the existing commands; calls the `architect-test` agent.
- `architect-test` agent — a copy of the base `architect` that surfaces Assumptions, Open Questions, and Non-Obvious Side Effects, and emits a machine-readable `CLARIFICATIONS_NEEDED:` block so the command can gate the pipeline on decision-forcing questions before implementation.

## [0.0.2]

### Added

- `project-manager-auto` slash command — a variant of the dev loop where planning runs inside Claude Code plan mode, so the user reviews the drafted plan and then picks "auto-accept edits" at the plan-mode approval dialog to run the implementation, QA, and review stages unattended.
- `architect-auto` agent — a read-only architect for the plan-mode flow that returns the design doc as text for the project manager to persist, rather than writing the plan file itself.

## [0.0.1] - 2026-06-18

### Added

- `project-manager` slash command — orchestrates the full end-to-end dev loop, routing tasks through planning, implementation, QA, review, and documentation stages.
- `architect` agent — analyses requirements and produces a structured implementation plan saved to a plan file before any code is written.
- `coder` agent — executes the architect's plan with precision, applying `Write`/`Edit` operations and self-correcting on unexpected errors.
- `qa-tester` agent — reviews newly written code for bugs, edge cases, missing error handling, and test-coverage gaps after implementation is complete.
- `reviewer` agent — audits code for security vulnerabilities, performance issues, and best-practice violations.
- `documenter` agent — updates technical documentation and appends a concise entry to `CHANGELOG.md` at closeout.

[Unreleased]: https://github.com/chrismou/claude-plugins/compare/v0.0.4...HEAD
[0.0.4]: https://github.com/chrismou/claude-plugins/compare/v0.0.3...v0.0.4
[0.0.3]: https://github.com/chrismou/claude-plugins/compare/v0.0.1...v0.0.3
[0.0.1]: https://github.com/chrismou/claude-plugins/releases/tag/v0.0.1
