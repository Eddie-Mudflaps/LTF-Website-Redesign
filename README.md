# The Big Dumper

A personal practice and code-dump workspace.

## System optimization profile

This workspace is tuned for the current target laptop:

- **CPU:** Intel Core Ultra 9 288V, 64-bit x64
- **Memory:** 32 GB RAM
- **GPU:** Intel Arc 140V integrated GPU
- **Storage:** 954 GB total, with about 213 GB free at the time of tuning
- **Input:** pen and 10-point touch support

### Recommended defaults

Use these defaults for local development and experiments on this system:

| Area | Optimized setting | Why |
| --- | --- | --- |
| Parallel builds/tests | 10-12 worker threads | Leaves headroom for the OS while still using the high-core-count CPU effectively. |
| Memory-heavy jobs | Cap individual jobs around 20-24 GB RAM | Prevents swapping and keeps the machine responsive with 32 GB installed. |
| GPU workloads | Prefer Intel Arc/oneAPI, OpenVINO, or DirectML backends when available | Matches the Intel Arc 140V GPU instead of assuming NVIDIA CUDA support. |
| Storage hygiene | Keep at least 100 GB free | The drive is already heavily used, so large generated outputs, caches, and datasets should be pruned regularly. |
| Generated artifacts | Put build outputs, temporary dumps, datasets, and model caches outside Git | Keeps the repository lightweight and avoids committing machine-specific or oversized files. |
| UI experiments | Account for touch and pen input targets | The device supports touch, so interactive demos should avoid mouse-only controls where practical. |

### Tooling notes

- Prefer 64-bit toolchains and runtimes.
- Avoid CUDA-only dependencies unless an alternate CPU, DirectML, OpenVINO, or Intel GPU path is also available.
- For scripts that expose a `--workers`, `--jobs`, or `-j` option, start with `10` and increase only if CPU, memory, and thermals remain stable.
- For large experiments, write outputs to a configurable data/cache directory and document cleanup commands.
