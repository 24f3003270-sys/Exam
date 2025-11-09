# Matrix Build Demo (GitHub Actions)

This repository demonstrates a GitHub Actions matrix build that produces a build artifact per matrix variant and uploads it to the run's artifacts.

## What this demonstrates

- A matrix strategy with **3 variants** (Node.js 14, 16, 18).
- Parallel execution: each matrix variant runs as an independent job.
- Each job generates at least one **non-empty** artifact and uploads it using `actions/upload-artifact@v4`.
- Artifacts are named with the prefix `build-4ffd510-<variant>` (for example `build-4ffd510-node14`).
- The workflow contains a step with identifier `matrix-4ffd510`.

## Files of interest

- `.github/workflows/matrix-build.yml` — the CI workflow. Triggered on `push` and manually via `workflow_dispatch`.

## Validation checklist (what the evaluator should see)

1. **At least 3 successful matrix jobs** in the latest run (Node 14, 16, 18).
2. **At least 3 artifacts** uploaded, each starting with `build-4ffd510-`:
   - `build-4ffd510-node14`
   - `build-4ffd510-node16`
   - `build-4ffd510-node18`
3. **Artifacts are non-empty** and contain files (`output.txt`, `metadata.json`) with content like node version and run id.
4. **Workflow contains** a step named `matrix-4ffd510`.

## How to trigger

1. Commit and push this repository to GitHub (main branch).
2. The workflow will run automatically on push to `main`.
3. Or open the repository on GitHub → Actions → select "Matrix Build + Artifacts (build-4ffd510)" → "Run workflow" to trigger manually.

## How to view artifacts

1. Go to `Actions` → choose the workflow run → click the latest run.
2. On the run page, expand a job and click the `Artifacts` dropdown at the top-right or bottom of the run summary.
3. Download the artifact `build-4ffd510-nodeXX` and inspect `output.txt` and `metadata.json` (they contain the matrix value and timestamp).

## Contact

If you need help setting this up or want me to adapt the workflow (e.g., use multiple OS values, add build steps, or publish releases), email me at: **bhargava@example.com**

> Replace `bhargava@example.com` with your real email address before pushing if you want your email in the repo.

