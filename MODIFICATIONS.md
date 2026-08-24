# Modifications to Upstream Qt / PySide6 / shiboken6

**None.** GLB QuickRename does not patch, fork, recompile, or otherwise
modify Qt, PySide6, or shiboken6 in any way. It consumes the official,
unmodified prebuilt PySide6 6.11.2 wheel (which bundles its own Qt 6.11.2
binaries and shiboken6) exactly as published on PyPI, via a plain
`pip install`.

## Evidence

- `pip show PySide6` in the application's build virtual environment reports
  the install location as the standard `site-packages` path, with no
  `Editable project location` field -- i.e. a normal, unmodified wheel
  install, not a local/editable/patched source checkout.
- A search of the GLB QuickRename repository's entire git history for any
  `*.patch` file, a `vendor/` or `third_party/` directory, or any other
  sign of a locally-modified Qt/PySide6/shiboken6 copy found nothing.
- `requirements.txt` (previously `PySide6>=6.6`, now pinned to
  `PySide6==6.11.2`) installs PySide6 the same way as any other Python
  dependency -- there is no custom build step, patch application, or
  source modification anywhere in the build process (`build.bat` /
  `build_pro.bat`), which only run `pip install` followed by `pyinstaller`.
- The application's own PyInstaller `.spec` files (`GLBQuickRename.spec`,
  `GLBQuickRenamePro.spec`) only *select which already-built files* from
  the installed wheel get packaged (see the license-audit history for why
  Qt Virtual Keyboard, QtNetwork, QtQml/Quick, QtOpenGL, QtSvg, and QtPdf
  are excluded) -- this is packaging-time file selection, not source
  modification. None of the Qt/PySide6/shiboken6 binaries themselves are
  edited, re-linked, or rebuilt.

Because nothing is modified, no patch files accompany the source archives
in this compliance repository -- the archives are the complete,
unmodified upstream source, byte-identical to what Qt Project and the
PySide project themselves publish for version 6.11.2.
