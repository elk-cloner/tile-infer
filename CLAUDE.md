# tile-infer

LLM kernels in NVIDIA's tile programming model. See `README.md` for the layout.

## Conventions

- Take toolchain versions from TileGym's lockfile. The image builds from TileGym `main`.
- Test each kernel against a PyTorch reference.
- Time benchmarks on warm runs, because the first launch includes JIT. Use CUPTI for device time.
- Do not commit model weights, profiler captures or secrets.
