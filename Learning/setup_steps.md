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
9. **Question:** Data is at SKU × locality. Locality is likely too fine a
   grain — not enough price movement per SKU-locality to estimate elasticity
   reliably, and city × SKU is the more usable output anyway. What grain
   should we model and report at?
   **Answer:** Move both modeling and output to city × SKU. Aggregate the
   raw sales/price rows up from locality to city *before* fitting — don't
   fit a model per locality and then average results, since sparse locality
   models produce noise, not signal. Before aggregating, check whether price
   actually varies independently across localities in the same city, or is
   set once per city: if it's the same city-wide, aggregating loses nothing;
   if it really differs by locality at the same time, a plain average price
   can mask the exact variation that identifies elasticity. If locality-level
   price variation turns out to matter, a hierarchical model (locality
   nested inside city × SKU) is a fallback — it lets sparse localities
   borrow strength from others in the same city instead of losing that
   detail, while still reporting at city × SKU.
