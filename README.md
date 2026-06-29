# MinerUI Portable

[![Release](https://img.shields.io/github/v/release/Seezees/MinerUI-Portable?include_prereleases&sort=semver)](https://github.com/Seezees/MinerUI-Portable/releases)
[![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D4?logo=windows11)](#system-requirements)
[![MinerU](https://img.shields.io/badge/MinerU-3.4.0-orange)](https://github.com/opendatalab/MinerU)
[![Portable](https://img.shields.io/badge/portable-one%20folder-00b894)](docs/PORTABLE.md)
[![License](https://img.shields.io/badge/license-MinerU%20Open%20Source%20License-blue)](LICENSE.md)

**MinerUI Portable** is a Windows portable desktop wrapper for [MinerU](https://github.com/opendatalab/MinerU) 3.4.0.

The goal is simple: unpack one folder, run one executable, keep all heavy runtime files inside that same folder, and delete the folder when you no longer need it.

This project is **not the upstream MinerU project**. It packages MinerU for a portable Windows desktop workflow and adds a Tauri-based launcher for installation, Torch backend selection, cleanup and local WebUI startup.

## What it does

- Runs MinerU Gradio WebUI in a desktop window.
- Installs local `uv`, Python 3.12 and a local `.venv` automatically.
- Uses the original `mineru-3.4.0-py3-none-any.whl` placed next to the executable.
- Lets you choose Torch backend: CPU, CUDA auto, CUDA 12.6 or CUDA 12.8.
- Keeps runtime files inside the portable folder: `.venv`, `.cache`, `.tools`, `models`, `outputs`, `logs`.
- Provides cleanup buttons for Torch/MinerU, uv cache, models, outputs or the whole runtime.
- Shows live installation/startup logs in the launcher UI.
- Supports multi-language launcher UI; MinerU Gradio itself may still fall back to the languages supported by upstream MinerU.

## Download

Open the [Releases](https://github.com/Seezees/MinerUI-Portable/releases) page and download the portable archive from the latest release.

Recommended asset name:

```text
MinerUI-Portable-v1.0.0-win10-11.zip
```

## Quick start

1. Download the portable archive from Releases.
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

Deleting this folder removes the portable runtime.

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
