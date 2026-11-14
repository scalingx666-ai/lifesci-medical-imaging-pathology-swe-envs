# Issue

**Title:** Add CVaR upper constraint helper in Optimization

## Description

Usage

- JSON configuration:
  - Add a constraint entry with `"type": "CVaR_Upper"`.
  - Required fields:
    - `parameters.structure_name` (e.g., `"HEART"`)
    - `parameters.alpha` (e.g., `0.90`)
    - `constraints.limit` (CVaR upper limit on total dose, in Gy)

- Programmatic API:
  - Construct an `Optimization` object using the standard workflow.
  - Add the constraint, for example:
    `opt.add_CVaR_Upper(alpha=0.90, limit=5, struct="HEART")`
  - Solve the optimization problem using the existing solve workflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `319661307a3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.