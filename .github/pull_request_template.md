<!-- One idea per PR. See CONTRIBUTING.md. Security issues go through SECURITY.md, not a PR. -->

## Type

- [ ] Experiment (change to `train.py`)
- [ ] Docs / protocol (`README`, `program.md`, …)
- [ ] Fixed-area change (`prepare.py` / `runtime.py`) — agreed in issue #

## Hypothesis

<!-- One hypothesis, one main variable. For non-experiment PRs, describe the change and why. -->

## Change

<!-- What you changed in `train.py` (or elsewhere). -->

## Result

<!-- Experiments only. Default seed 42. -->

| | Baseline | This PR |
| --- | --- | --- |
| `val_bpb` | | |
| `peak_vram_mb` | | |
| tok/sec | | |

- Device:
- Number of runs (architecture changes: 2–3 recommended):

## Checklist

- [ ] Diff is confined to `train.py`, or this is a docs / agreed fixed-area change
- [ ] Improvement beats the noise threshold (> 0.02 bpb for hyperparameter/optimizer changes, > 0.05 or averaged runs for architecture changes)
- [ ] `train.py` runs end to end on at least one device
- [ ] No `results.tsv`, `run*.log` or other local files committed
