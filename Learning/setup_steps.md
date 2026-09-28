# Setup steps so far

1. Pushed an empty initial commit to `main` (remote started blank).
2. Added README stating the repo's goal: build and test ML models, starting
   with elasticity and Bayesian causal inference.
3. Set up a Python 3.11 venv. Fixed a broken `gc_core` path in
   `requirements.txt` (it now points to the `ds-models` sibling repo).
   Installed and verified all packages.
4. Added `.gitignore`, documented environment setup in README.
5. Created `Notebooks/`, `Input/`, `Output/` folders. Notebooks are the core
   deliverable: each one covers one logical stage and saves its output,
   which the next notebook reads as input.
6. Split `Input/` into `brand_specific/` (per-brand configs) and `common/`
   (inputs shared across all brands).
7. Decided per-brand configs (model scope, SKUs, parameters) are stored as
   YAML, one file per brand — readable, editable, supports comments, unlike
   JSON.
8. Added this `Learning/` folder to keep a running log of steps taken.
