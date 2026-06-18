# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.1] - 2026-06-18

### Added

- `project-manager` slash command — orchestrates the full end-to-end dev loop, routing tasks through planning, implementation, QA, review, and documentation stages.
- `architect` agent — analyses requirements and produces a structured implementation plan saved to a plan file before any code is written.
- `coder` agent — executes the architect's plan with precision, applying `Write`/`Edit` operations and self-correcting on unexpected errors.
- `qa-tester` agent — reviews newly written code for bugs, edge cases, missing error handling, and test-coverage gaps after implementation is complete.
- `reviewer` agent — audits code for security vulnerabilities, performance issues, and best-practice violations.
- `documenter` agent — updates technical documentation and appends a concise entry to `CHANGELOG.md` at closeout.
- Plan-mode integration — the architect runs inside Claude Code plan mode so the user can review and approve the plan before the coder begins implementation.

[Unreleased]: https://github.com/chrismou/claude-plugins/compare/v0.0.1...HEAD
[0.0.1]: https://github.com/chrismou/claude-plugins/releases/tag/v0.0.1
