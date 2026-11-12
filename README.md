# Roda's AI Safety Playground

A personal learning space for exploring AI safety papers through small,
reproducible Python/Jupyter experiments. The aim is to understand core issues,
assumptions, and methodologies, not to claim new research or safety guarantees.

Three overlapping lenses guide the exploration: **misuse** (harmful use),
**misalignment** (objectives diverging from intent), and **systemic risk**
(failures arising across interacting systems and institutions).

Work here is exploratory. Toy demonstrations are not paper replications or
evidence that a system is safe.

## Start here

Use Python 3.12. From the repository root:

```powershell
python -m venv .venv
.\.venv\Scripts\python -m pip install -r requirements.txt
.\.venv\Scripts\python -m jupyterlab
```

On macOS/Linux, use `.venv/bin/python` in place of `.\.venv\Scripts\python`.

## Navigate and experiment

- [`notebooks/basics.ipynb`](notebooks/basics.ipynb): start here. Small offline
  exercises cover sampling, reasoning-trace checks, instruction boundaries,
  proxy rewards, and correlated failures, with saved visual results.
- `notebooks/00-template.ipynb`: copy to a descriptive name for each experiment.
  It prompts for sources, a testable hypothesis, baselines, methods, results,
  and limitations; it contains no research results.
- `requirements.txt`: pinned notebook tools, not a fully locked environment.
  Add experiment-specific dependencies only when needed.
- `LICENSE`: MIT for original work; cited papers and external data retain their
  own licenses.

Learning starting points: [AI Safety Map](https://aisafety.com/map) and
[BlueDot technical AI safety](https://bluedot.org/courses/technical-ai-safety).
Paper references sit beside the relevant notebook exercises.

Before interpreting results, record the paper version, data provenance/license,
seed, Python/package versions, and relevant hardware. For an exact package
snapshot, run `.\.venv\Scripts\python -m pip freeze` and save it alongside the
experiment as `<experiment>.requirements.txt`. Restart the kernel and run all
cells in order before sharing.

Keep experiments local and use synthetic or explicitly shareable data. Do not
commit credentials, private data, model weights, or large generated files.
Local `data/`, `artifacts/`, environments, and caches are ignored; describe how
to obtain or regenerate any required inputs. Clear notebook outputs before
committing unless they are small, reviewed, and essential to understanding
(as in `basics.ipynb`). No model downloads, credentials, or network calls are
needed to run the basics.
