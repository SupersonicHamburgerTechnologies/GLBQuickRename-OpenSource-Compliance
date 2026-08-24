# Source Provenance

## Qt (qtbase, qtimageformats)

Downloaded from Qt's own official release server:

```
https://download.qt.io/official_releases/qt/6.11/6.11.2/submodules/qtbase-everywhere-src-6.11.2.tar.xz
https://download.qt.io/official_releases/qt/6.11/6.11.2/submodules/qtimageformats-everywhere-src-6.11.2.tar.xz
```

Each has an official `.sha256` sidecar file published alongside it at the
same URL (append `.sha256`). Both downloaded archives were verified to
match those officially published checksums exactly before being re-hosted
here -- see `SHA256SUMS.txt`. This confirms the archives are unmodified,
official Qt Project releases, not a mirror substitution or a tampered copy.

## Qt for Python (PySide6 / shiboken6)

PySide6 6.11.2 has no source distribution (sdist) published on PyPI --
only prebuilt platform wheels. The actual source lives in the
`pyside-setup` super-repository (which directly contains both
`sources/pyside6` and `sources/shiboken6`, not as git submodules), and Qt
Project publishes an official packaged snapshot of it -- the same
"-everywhere-src-" naming convention used for qtbase/qtimageformats above
-- directly on its own release server:

```
https://download.qt.io/official_releases/QtForPython/pyside6/PySide6-6.11.2-src/pyside-setup-everywhere-src-6.11.2.tar.xz
```

This has an official `.sha256` sidecar file published alongside it at the
same URL (append `.sha256`), exactly like the Qt archives above. The
downloaded archive was verified to match that officially published
checksum exactly before being re-hosted here:

```
cba47efbaad1bedd529725cbc14e21f156c7a19366f07b3edfbb076ffd7afdf8  pyside-setup-everywhere-src-6.11.2.tar.xz
```

This confirms the archive is an unmodified, official Qt Project release,
not a mirror substitution or a tampered copy -- the same standard of
verification as the qtbase/qtimageformats archives, rather than relying on
a GitHub mirror's auto-generated (and not independently checksummed) tag
archive, which an earlier draft of this repository had used before being
replaced with this official release-server copy.

## Version match to what's actually shipped

- `PySide6.__version__`, `PySide6.QtCore.qVersion()`, and
  `shiboken6.__version__` were all confirmed to report exactly `6.11.2` in
  the build environment used to produce the shipped GLB QuickRename /
  GLB QuickRename Pro binaries.
- `requirements.txt` now pins `PySide6==6.11.2` exactly (previously
  `PySide6>=6.6`, which would have let a future rebuild silently drift onto
  a newer PySide6/Qt release without this compliance repository's archives
  following along). A clean-venv reinstall from the pinned requirement was
  used to confirm PySide6, PySide6_Essentials, PySide6_Addons, and
  shiboken6 all resolve to exactly 6.11.2 before rebuilding the shipped
  binaries. The pin should be bumped, and this repository's archives
  refreshed to match, together as one change whenever the bundled Qt
  version changes in the future.
