---
name: projectmanager
description: Interactive End-to-End Dev Loop
---
# Task: $ARGUMENTS

### 1. Planning
- **ARCHITECT:** Call 'architect' to analyze "$ARGUMENTS". It will write a plan to `plans/YYYYMMDD-slug.md` and return the path as `PLAN_PATH: ...`.
- **PAUSE:** "Plan generated at [PLAN_PATH]. Review/Edit it, then type 'GO' to start coding."

### 2. Implementation
- **CODER:** Call 'coder' to execute the plan.
- **QA:** Call 'qa-tester' to verify the work. If QA fails, return to CODER.

### 3. Review
- **REVIEWER:** Call 'reviewer' to check for style/security.
- **PAUSE:** "Work is complete. Review the diffs. Are you happy? (Yes/No)"

### 4. Closeout
- **IF YES:** Call 'documenter' to update docs. Do NOT delete the plan file — it is retained for audit and version control.
- **IF NO:** Ask for feedback and loop back to Step 1.
