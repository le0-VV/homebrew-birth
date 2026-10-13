# Homebrew tap for Birth

A community-maintained cask for [Birth](https://github.com/iAmCorey/birth), an open-source macOS startup item manager. It installs the official universal DMG for Apple Silicon and Intel Macs and requires macOS 14 (Sonoma) or later.

## Install

```bash
brew install --cask le0-VV/birth/birth
```

Birth is not notarised by Apple. If macOS blocks the first launch, open System Settings → Privacy & Security and select **Open Anyway**.

## Upgrade

```bash
brew update
brew upgrade --cask le0-VV/birth/birth
```

After upgrading, re-grant Full Disk Access and Automation permissions in System Settings by toggling Birth off and back on, as documented by the project.

## Uninstall

```bash
brew uninstall --cask le0-VV/birth/birth
```

Add `--zap` to remove preferences too. Removal backups in `~/Library/Application Support/Birth` are preserved, including with `--zap`.

## Maintenance

For each stable [upstream release](https://github.com/iAmCorey/birth/releases), update `version` and `sha256` in `Casks/birth.rb`. Download the official DMG and calculate its checksum with `shasum -a 256` before committing. Release updates are manual.

Validate changes with:

```bash
brew style --cask le0-VV/birth/birth
brew audit --cask --strict --online le0-VV/birth/birth
brew fetch --cask le0-VV/birth/birth
```

Report application bugs [upstream](https://github.com/iAmCorey/birth/issues) and packaging issues [in this tap](https://github.com/le0-VV/homebrew-birth/issues).
