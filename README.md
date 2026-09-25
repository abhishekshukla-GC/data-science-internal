# data-science-internal

Repo for building and testing machine learning models.

Starting point: price elasticity models using Bayesian causal inference.
More model work will be added on top of this over time.

## Structure

The notebooks are the main thing here — each one covers one logical stage of
a pipeline and saves its result to disk. The next notebook picks that up as
its input. This keeps each stage runnable and inspectable on its own instead
of one long script.

- `Notebooks/` — the `.ipynb` files, numbered by stage (e.g.
  `01_elasticity.ipynb`, `02_...ipynb`). This is where the real work happens.
- `Input/` — raw input data for the pipeline.
- `Output/` — each notebook's saved result, read as input by the next
  notebook in the sequence.

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
