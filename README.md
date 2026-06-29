# MinerUI Portable

[![Release](https://img.shields.io/github/v/release/Seezees/MinerUI-Portable?include_prereleases&sort=semver)](https://github.com/Seezees/MinerUI-Portable/releases)
[![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D4?logo=windows11)](#system-requirements)
[![MinerU backend](https://img.shields.io/badge/MinerU_backend-3.4.0-orange)](#supported-backends)
[![Portable](https://img.shields.io/badge/portable-one%20folder-00b894)](docs/PORTABLE.md)
[![License](https://img.shields.io/badge/license-MinerU%20Open%20Source%20License-blue)](LICENSE.md)

**MinerUI Portable** is a portable Windows desktop launcher for **MinerU 3.4.0**.

It is made for the case where you do not want a global Python setup, a system-wide install, or a scattered AI toolchain. Unpack one folder, run one executable, keep all runtime files inside that folder, and delete the folder when you no longer need it.

This repository is **not the upstream MinerU project**. It is a portable desktop packaging/wrapper project around the upstream MinerU Python package and Gradio UI.

## Why this exists

Upstream MinerU is powerful, but a local Windows setup can become heavy and messy: Python, Torch, model cache, package cache and outputs may end up spread across the machine.

MinerUI Portable keeps that runtime contained:

```text
MinerUI-Portable/
  MinerUI Portable.exe
  mineru-3.4.0-py3-none-any.whl
  config/
  .venv/
  .cache/
  .tools/
  models/
  outputs/
  logs/
```

## Features

- Portable one-folder Windows runtime.
- Tauri desktop launcher for MinerU Gradio WebUI.
- Automatic local `uv` bootstrap.
- uv-managed Python 3.12.
- Local `.venv` for MinerU, Torch and dependencies.
- Torch backend selector:
  - CPU
  - CUDA auto
  - CUDA 12.6
  - CUDA 12.8
- Live installation and startup log inside the launcher.
- Runtime cleanup buttons for `.venv`, `.cache\uv`, models, outputs or all runtime data.
- Multi-language launcher UI.
- Uses the original MinerU 3.4.0 wheel placed next to the executable.

## Supported backends

MinerUI Portable has two separate meanings of “backend”:

1. **MinerU backend version** — the MinerU Python package/wheel used by this portable release.
2. **Torch backend** — CPU/CUDA wheel selection used by PyTorch inside the local MinerU environment.

### MinerU backend support

| Component | Supported in v1.0.0 | Notes |
|---|---:|---|
| MinerU backend | **3.4.0** | Primary supported version. Uses `mineru-3.4.0-py3-none-any.whl`. |
| MinerU Gradio UI | **3.4.0** | Launched locally through the portable environment. |
| MinerU local API/runtime | **3.4.0-compatible** | Managed by upstream `mineru-gradio`/MinerU code. |
| Other MinerU versions | Not guaranteed | May work only after changing the wheel/version and rebuilding/testing. |

### Torch backend support

| Launcher option | `UV_TORCH_BACKEND` | Use case | Size/performance |
|---|---|---|---|
| CUDA auto | `auto` | Default mode for supported NVIDIA setups | Larger download, faster if CUDA works |
| CUDA 12.6 | `cu126` | Pin CUDA 12.6 wheels | Larger download |
| CUDA 12.8 | `cu128` | Pin CUDA 12.8 wheels | Larger download |
| CPU | `cpu` | Smaller install, no CUDA dependency | Smaller, slower |

Changing CPU/CUDA cleanly usually requires deleting `.venv` from the launcher UI and starting again.

## Download

Open the Releases page and download the portable archive from the latest release.

Recommended asset name:

```text
MinerUI-Portable-v1.0.0-win10-11.zip
```

## Quick start

1. Download the portable archive.
2. Extract it to a writable folder, for example:

   ```text
   D:\Tools\MinerUI-Portable
   ```

3. Run:

   ```text
   MinerUI Portable.exe
   ```

4. Choose a Torch backend.
5. Press **Install and start**.
6. Wait for the local MinerU WebUI to open.

First launch can take a long time because Python packages, Torch and MinerU models may need to be downloaded.

## System requirements

- Windows 10 or Windows 11, x64.
- Internet connection for first-time installation and model/package downloads.
- Free disk space depending on backend:
  - CPU mode: smaller, slower.
  - CUDA mode: larger, faster on supported NVIDIA GPUs.
- Microsoft Edge WebView2 Runtime, usually already installed on modern Windows.

## Portable layout

After first launch, the app folder may look like this:

```text
MinerUI-Portable/
  MinerUI Portable.exe
  mineru-3.4.0-py3-none-any.whl
  config/
    launcher.env
  .venv/        # MinerU, Torch and Python packages
  .cache/       # uv/pip/cache data
  .tools/       # local uv and uv-managed Python
  models/       # model cache
  outputs/      # conversion results
  logs/         # launcher and MinerU logs
```

Torch is installed inside:

```text
.venv\Lib\site-packages\torch
```

Downloaded wheels/cache are stored in:

```text
.cache\uv
```

More details: [docs/PORTABLE.md](docs/PORTABLE.md).

## Build from source

For users who want to build the portable package locally:

```bat
build-portable-package.bat
```

The output is:

```text
dist\portable\MinerUI Portable.exe
dist\MinerUI-Portable.zip
```

The source-only development build is separate:

```bat
build-dev-exe-only.bat
```

## Troubleshooting

See [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md).

The most useful log file is:

```text
logs\mineru-desktop.log
```

## Relationship to MinerU

MinerUI Portable is based on MinerU 3.4.0 and uses the upstream MinerU Python package and Gradio UI.

Original project:

- Repository: https://github.com/opendatalab/MinerU
- Documentation: https://opendatalab.github.io/MinerU/
- Homepage: https://mineru.net/

See [NOTICE.md](NOTICE.md) and [LICENSE.md](LICENSE.md) for licensing and attribution.

## License

MinerUI Portable follows the license terms of MinerU for the included MinerU code/package. See [LICENSE.md](LICENSE.md) and [NOTICE.md](NOTICE.md).
