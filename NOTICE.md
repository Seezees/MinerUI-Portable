# Notice

MinerUI Portable is a Windows portable desktop wrapper and packaging project for MinerU.

This repository is based on and depends on the upstream MinerU project:

- Upstream repository: https://github.com/opendatalab/MinerU
- Upstream documentation: https://opendatalab.github.io/MinerU/
- Upstream homepage: https://mineru.net/

MinerUI Portable does not claim ownership over MinerU. The MinerU Python package, model workflows, Gradio application and related MinerU code remain under the upstream MinerU project's license and attribution requirements.

## Included / used upstream component

- MinerU version: 3.4.0
- Package file used by the portable launcher: `mineru-3.4.0-py3-none-any.whl`
- Upstream Python package name: `mineru`

## Portable wrapper component

MinerUI Portable adds a Windows-focused launcher/runtime wrapper around MinerU:

- Tauri desktop launcher.
- Portable runtime folder layout.
- Local `uv` and uv-managed Python bootstrap.
- Torch backend selection.
- Runtime cleanup tools.
- Release packaging scripts for a Windows portable zip.

## License note

The upstream repository currently includes `LICENSE.md` with the MinerU Open Source License text. This repository keeps that license file for MinerU-derived code and package usage.

If you redistribute this repository or release archives, keep:

- `LICENSE.md`
- `NOTICE.md`
- attribution to https://github.com/opendatalab/MinerU

## Third-party dependencies

The portable runtime downloads and installs third-party Python packages such as Torch, Gradio, FastAPI, transformers and related dependencies via `uv`. Those dependencies are governed by their own licenses.

The release archive should not be treated as a single-license binary bundle unless all included dependencies have been reviewed separately.
