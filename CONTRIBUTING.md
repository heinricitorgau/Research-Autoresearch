# Contributing

Thanks for your interest in Research-Autoresearch. This repo is a fixed-budget experiment loop: every training run gets the same 5 minutes, and ideas are judged only by `val_bpb`. Contributions should keep that loop clean and comparable.

## Local setup

Requirements: Python 3.10+, and an NVIDIA GPU, Apple Silicon, or CPU.

With [uv](https://docs.astral.sh/uv/):

```bash
uv sync
uv run prepare.py   # one-off: downloads data shards and trains the tokenizer
uv run train.py     # one baseline run (~5 minutes of training)
```

On Windows + NVIDIA you can use the system Python and pip instead:

```powershell
pip install torch --index-url https://download.pytorch.org/whl/cu126
pip install rustbpe tiktoken pyarrow requests pandas matplotlib "triton-windows<3.3"
python prepare.py
python train.py
```

See the README for device-specific notes. A run is healthy when it finishes and prints `val_bpb`.

## Where changes go

| File | Role | Can you change it? |
| --- | --- | --- |
| `train.py` | Model, optimizer, hyperparameters, training loop | Yes — this is the experiment surface |
| `prepare.py` | Data, tokenizer, evaluation | Only by discussing it in an issue first |
| `runtime.py` | Device detection, attention backend, compile, VRAM tiers | Only by discussing it in an issue first |
| `program.md` | Research protocol | Yes, for protocol clarifications |

Changing `prepare.py` or `runtime.py` changes what every past result means, so those changes need agreement before code.

## Adding an experiment

Follow the protocol in `program.md`:

1. Write down one hypothesis and its single main variable.
2. Change `train.py` only.
3. Run it with the default seed (42) and record `val_bpb`, `peak_vram_mb`, and throughput.
4. Keep it only if it beats the baseline by more than the noise:
   - hyperparameter / optimizer-only changes: improve by **> 0.02** bpb;
   - architecture changes (these re-draw the initialization): improve by **> 0.05** in one run, or average 2–3 runs.
5. Discard everything that does not pass. A clean history of kept ideas is the goal.

`results.tsv` and `run*.log` are local and are not committed.

## Pull requests

- One idea per PR. Do not mix an experiment with refactors or formatting changes.
- Describe the hypothesis, the change, and the result: baseline vs. new `val_bpb`, peak VRAM, tokens/sec, device, and how many runs.
- Keep the diff confined to `train.py` unless the PR is about docs or an agreed change to the fixed area.
- Make sure `train.py` still runs end to end on at least one device.
- Use short, imperative commit messages (for example `train: lower warmup to 200 steps`).
- Bugs and data problems go through the issue templates; security problems go through [SECURITY.md](SECURITY.md).

By contributing you agree that your contributions are licensed under the [MIT License](LICENSE) and that you will follow the [Code of Conduct](CODE_OF_CONDUCT.md).
