# Image

A development image for [TileGym](https://github.com/NVIDIA/TileGym). It is built from TileGym's own `modeling/transformers/Dockerfile`, at the current `main` branch. TileGym's lockfile sets the toolchain versions.

The image needs an amd64 host with a Blackwell GPU and a driver that supports CUDA 13.

## Build

Run the **Build image** workflow from the Actions tab, or:

```bash
gh workflow run build-image.yml
```

Each run pushes two tags to `ghcr.io/elk-cloner/tile-infer`:

| Tag | Points to |
| --- | --- |
| `main` | The most recent build |
| `main-<commit>` | The build from that TileGym commit |

## Run

```bash
docker run --rm -it --gpus all ghcr.io/elk-cloner/tile-infer:main bash
```

TileGym is at `/workspace/tilegym`, without its `.git` directory. The shell starts in `modeling/transformers`, where the `uv` environment lives.

```bash
# Kernel tests
uv run --locked --no-sync python -m pytest /workspace/tilegym/tests/ops -k test_op -n 4

# One benchmark
cd /workspace/tilegym/tests/benchmark
uv run --locked --no-sync --project /workspace/tilegym/modeling/transformers python bench_rmsnorm.py

# Inference
uv run --locked --no-sync tilegym-hf-bench --help
```
