# Report Queue Simulator

Real-time browser simulation of reporting load. Reports enter a queue and are
processed by Kubernetes pods across configurable memory tiers. A report that
exceeds its pod's RAM budget (pod RAM − 100 MB overhead) is killed and restarts
from scratch on a larger tier. Memory and runtime are correlated and derived
from real 30-day production distributions.

Open `index.html` in a browser — no build, no dependencies. All CSS/JS is
inline and the data is baked into the page.

## Features

- Log-scaled load control, defaulting to the real ~0.03 reports/s mean.
- Dynamic pod tiers (1–6), k8s-style node bin-packing with real Azure VM costs.
- Burst injector with `1×/2×/4×/8× BigY` presets and per-batch completion stats
  (time to first/last report, average per report, etc.).
- Live charts: arrivals vs throughput, and per-tier queue depth.

## GitHub Pages

**Settings → Pages → Deploy from a branch → `main` / root.** Served at
`https://<you>.github.io/<repo>/`.

## Data

The distributions in `instance_sizes.csv`, `memory_percentiles.csv`, and
`timing.csv` are the source of truth; they are baked into `index.html` at author
time and are **not** fetched at runtime.
