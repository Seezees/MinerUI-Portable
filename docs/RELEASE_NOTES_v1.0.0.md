# MinerUI Portable v1.0.0

**Based on MinerU 3.4.0.**

MinerUI Portable v1.0.0 is the first public portable Windows release of the MinerUI desktop wrapper for MinerU.

## Recommended download

Download the release asset:

```text
MinerUI-Portable-v1.0.0-win10-11.zip
```

Extract it to a writable folder and run:

```text
MinerUI Portable.exe
```

## Highlights

- Portable Windows runtime: one folder, one executable.
- Local Tauri launcher for MinerU Gradio WebUI.
- Uses original MinerU 3.4.0 wheel.
- Local `uv` bootstrap.
- uv-managed Python 3.12.
- Torch backend selector:
  - CPU
  - CUDA auto
  - CUDA 12.6
  - CUDA 12.8
- Runtime cleanup from the launcher UI:
  - `.venv` / Torch / MinerU packages
  - `.cache\uv`
  - models
  - outputs
  - all runtime data
- Multi-language launcher UI.
- Live logs in the launcher window.
- Runtime data stays inside the portable folder.

## Portable folders

The app keeps heavy runtime files here:

```text
.venv
.cache
.tools
models
outputs
logs
```

Delete the portable folder to uninstall.

## Known notes

- First launch can take a long time because Torch, MinerU dependencies and models may be downloaded.
- CUDA backend downloads are much larger than CPU backend downloads.
- MinerUI Portable is a wrapper/packaging project; MinerU itself remains the upstream project by OpenDataLab.

## Upstream

- MinerU repository: https://github.com/opendatalab/MinerU
- MinerU documentation: https://opendatalab.github.io/MinerU/

## Suggested Git tag

```text
minerui-portable-v1.0.0
```

## Suggested release title

```text
MinerUI Portable v1.0.0 — based on MinerU 3.4.0
```
