# Troubleshooting

This page covers common MinerUI Portable problems.

## Where to find logs

The main log is:

```text
logs\mineru-desktop.log
```

When reporting a bug, attach this file or paste the relevant part.

## First launch takes a long time

Expected. First launch can download:

- uv
- Python 3.12
- Torch / torchvision
- MinerU dependencies
- MinerU models

CUDA backends are much larger than CPU backend.

## Internet connection breaks during Torch download

MinerUI Portable uses `uv` cache and retries. Start the app again; already downloaded files should be reused from:

```text
.cache\uv
```

If the cache becomes corrupted, clear `.cache\uv` from the launcher UI and retry.

## Switching from CUDA to CPU or CPU to CUDA

The selected backend affects the installed Torch wheel. To switch cleanly:

1. Select the new backend in the launcher.
2. Delete Torch/MinerU runtime from the launcher UI.
3. Start again.

This removes:

```text
.venv
```

and installs a new environment.

## The app opens but MinerU UI does not appear

Check:

1. `logs\mineru-desktop.log`
2. Whether port `127.0.0.1:7860` is already used by another program.
3. Whether antivirus/firewall blocked Python or the local server.

You can also open manually:

```text
http://127.0.0.1:7860
```

## CMD window flashes or remains open

The intended release build is a GUI executable. Build with:

```bat
build-portable-package.bat
```

Then run:

```text
dist\portable\MinerUI Portable.exe
```

Do not run internal Python or debug scripts unless you are diagnosing a problem.

## Disk usage is too high

Most space is usually used by:

```text
.venv
.cache\uv
models
```

Use the cleanup buttons in the launcher. The safest large cleanup is:

1. Delete `.venv` to remove Torch/MinerU packages.
2. Clear `.cache\uv` if you do not need package cache.
3. Delete `models` if you want to redownload models later.

## Build script cannot find Cargo

Install Rust from:

```text
https://rustup.rs/
```

Then open a new terminal and run:

```bat
build-portable-package.bat
```

## Build succeeds but portable zip is huge

The source build folder may contain old `target`, `.venv`, `.cache`, or runtime data. The portable output should be created in:

```text
dist\portable
```

Do not upload source build caches as release assets.

## What to include in a bug report

Please include:

- Windows version.
- CPU or CUDA backend.
- GPU model if using CUDA.
- Whether first launch or later launch failed.
- `logs\mineru-desktop.log`.
- Screenshot of the launcher if possible.
