# Portable runtime

MinerUI Portable is designed to run from one writable folder.

The application does not require a global Python installation and does not intentionally write heavy runtime files into system Python folders.

## Recommended install location

Use a short writable path, for example:

```text
D:\Tools\MinerUI-Portable
C:\Tools\MinerUI-Portable
```

Avoid paths that require administrator rights, such as:

```text
C:\Program Files\...
```

## Runtime layout

After first launch, the folder may contain:

```text
MinerUI-Portable/
  MinerUI Portable.exe
  mineru-3.4.0-py3-none-any.whl
  config/
    launcher.env
  .venv/
  .cache/
  .tools/
  models/
  outputs/
  logs/
```

## What each folder contains

| Path | Purpose |
|---|---|
| `.venv/` | Local Python virtual environment, MinerU, Torch and Python packages. |
| `.cache/uv/` | Downloaded Python wheels and uv cache. Helps resume/retry installs. |
| `.tools/uv/` | Local uv executable. |
| `.tools/python/` | uv-managed Python runtime. |
| `models/` | HuggingFace, ModelScope and Torch model cache. |
| `outputs/` | Converted documents/results. |
| `logs/` | Launcher and MinerU logs. |
| `config/launcher.env` | Launcher settings. |

## Where Torch is installed

Installed Torch package:

```text
.venv\Lib\site-packages\torch
```

Downloaded wheel/cache files:

```text
.cache\uv
```

## Changing CPU/CUDA backend

The safest way to change backend is:

1. Open `MinerUI Portable.exe`.
2. Choose another Torch backend.
3. Delete Torch/MinerU runtime from the UI, which removes `.venv`.
4. Press **Install and start** again.

This forces a clean reinstall with the chosen backend.

## Uninstall

Close the application and delete the whole portable folder.

## Moving the app

You can move the portable folder to another location. If the runtime behaves oddly after moving:

1. Delete `.venv`.
2. Keep `mineru-3.4.0-py3-none-any.whl` next to the exe.
3. Start the app again.

## What should not be committed to Git

Do not commit runtime folders:

```text
.venv/
.cache/
.tools/
models/
outputs/
logs/
dist/
```

They are intentionally ignored by `.gitignore`.
