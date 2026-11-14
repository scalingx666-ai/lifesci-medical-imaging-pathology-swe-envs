# Issue

**Title:** Fix Umami website ID and add custom event tracking

## Description

## Summary
The `data-website-id` in `web/templates/base.html` pointed to a site that doesn't exist in the Umami instance, so nothing was being recorded. This PR fixes that and adds custom events.

### 1. Fix website ID
- Created the "Brain Tumor Segmentation" site in Umami (domain `bts.subhajitdas.me`) and switched the script tag to its ID.
- Do-Not-Track is intentionally not honored (Umami's default).

### 2. Custom events
Fired through a guarded `window.track()` helper in `base.html` (no-ops if an ad blocker removes `window.umami`):

| Event | Properties |
|---|---|
| `predict-start` | `source` (sample/upload), `sample_id` or `file_type` |
| `predict-success` | `source`, `inference_ms`, `dice` (samples only) |
| `predict-error` | `source`, `status` (0 = network failure, 429 = rate limited) |
| `gallery-open` | `image_id`, `dice` |
| `github-click` | none (declarative `data-umami-event`) |

No filenames, image data, error text or uploader information is sent, consistent with the in-memory upload design. Events and the no-PII rule are documented in `CLAUDE.md`.

## Test plan
- [x] Locally, with a stubbed `window.umami`: sample click, bad upload (400), and gallery click emit the expected payloads; `track()` doesn't throw when `umami` is absent.
- [ ] After deploy, load https://bts.subhajitdas.me, exercise each action, and confirm the events and properties in Umami (real tracking is inert on localhost because of `data-domains`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed2dc9dc0fdd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.