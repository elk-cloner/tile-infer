# tile-infer

LLM kernels in NVIDIA's tile programming model, written with cuTile Python and cutile-rs. Kernels are checked against PyTorch and benchmarked against reference implementations.

## Layout

| Path | Holds |
| --- | --- |
| `docker/` | The pinned development image |
| `scripts/` | Setup and run helpers |
| `kernels/` | Kernels and their tests |
| `benchmarks/` | Benchmark harnesses |
| `writeups/` | Notes on kernels and results |
| `upstream/` | Local checkouts of related projects; not tracked |

## Requirements

An NVIDIA Blackwell GPU (sm_120) with a driver that supports CUDA 13. See [`docker/README.md`](docker/README.md) for versions.
