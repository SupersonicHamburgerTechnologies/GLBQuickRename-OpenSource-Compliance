# GLB QuickRename -- Open Source Compliance

This repository exists solely to satisfy the "Corresponding Source" and
license-notice obligations of the LGPLv3-licensed components bundled with
**GLB QuickRename** and **GLB QuickRename Pro** (the GLB texture/material
renaming utility). It does **not** contain GLB QuickRename's own source
code, which remains proprietary and unpublished.

Every archive under [Releases](../../releases) is the **unmodified,
official upstream source**, downloaded directly from Qt's own official
release server, for the exact version of each LGPLv3 component actually
bundled in the shipped application -- not a newer or older version, and
not a locally patched copy. GLB QuickRename does not patch, fork, or
modify Qt, PySide6, or shiboken6 in any way; it consumes the official
prebuilt PySide6 6.11.2 wheel from PyPI as-is. See `MODIFICATIONS.md` for
how that was confirmed.

## What's here

| Component | Version shipped | Archive | SHA-256 |
|---|---|---|---|
| Qt (QtCore, QtGui, QtWidgets base module) | 6.11.2 | `qtbase-everywhere-src-6.11.2.tar.xz` | see `SHA256SUMS.txt` |
| Qt (additional image-format plugins: TIFF, WebP) | 6.11.2 | `qtimageformats-everywhere-src-6.11.2.tar.xz` | see `SHA256SUMS.txt` |
| Qt for Python (PySide6) + shiboken6 | 6.11.2 | `pyside-setup-everywhere-src-6.11.2.tar.xz` | see `SHA256SUMS.txt` |

`SHA256SUMS.txt` in each release lists the exact checksum of every archive
in that release. All three archives were downloaded directly from Qt's own
official release server and verified against Qt's own officially published
`.sha256` sidecar file at the same URL before being re-hosted here --
see `PROVENANCE.md` for the exact URLs and checksums.

## Why a separate repository, and why release assets instead of a committed tree

- GLB QuickRename's own source is not public; this repository is scoped
  narrowly to third-party Corresponding Source obligations only, so it can
  be public on its own without exposing the application's source.
- These are large, unmodified upstream archives. Committing them into git
  history would bloat a repository that gains nothing from version-control
  diffing on binary-ish source tarballs. Release assets are the normal
  GitHub mechanism for exactly this ("attach a build artifact / large file
  to a tagged release") and keep the repository itself lightweight.

## Requesting these sources another way

If you'd prefer to obtain these sources directly from their original
publishers rather than from this repository, they remain available at:

- Qt: https://download.qt.io/official_releases/qt/6.11/6.11.2/submodules/
- Qt for Python (PySide6/shiboken6): https://download.qt.io/official_releases/QtForPython/pyside6/PySide6-6.11.2-src/
