# Issue

**Title:** Add Umami analytics tracking

## Description

## Summary
- Adds the self-hosted Umami tracking script (`https://umami.subhajitdas.me/script.js`) to `web/templates/base.html`, so every page (`/`, `/about`, `/gallery`, 404) is tracked from one place.
- Sets `data-domains="bts.subhajitdas.me"` so only production visits are counted; local dev traffic is ignored.
- Documents the analytics setup in `CLAUDE.md`.

## Before merging
- [x] Serve Umami over HTTPS (`umami.subhajitdas.me`) so the script isn't blocked as mixed content
- [x] Point the script `src` at the HTTPS URL
- [ ] After deploy, confirm a pageview shows up in the Umami dashboard

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01AD9EEEaTgHDLn4nVe2aCGL

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2719eb599b67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.