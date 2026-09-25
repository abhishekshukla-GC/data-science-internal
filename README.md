# data-science-internal

Repo for building and testing machine learning models.

Starting point: price elasticity models using Bayesian causal inference.
More model work will be added on top of this over time.

## Environment setup

Needs Python 3.11 (pins were captured against 3.11.15) and a checkout of
`ds-models` as a sibling folder, since `gc_core` is installed from there:

```bash
python3.11 -m venv .venv
.venv/bin/pip install -r requirements.txt
```

`requirements.txt` pins exact versions, not ranges — the elasticity numbers
come out of an XGBoost double-ML stage and a NumPyro/JAX Bayesian MCMC
sampler, and different library versions can change results even with the
same code, data, and seed.
