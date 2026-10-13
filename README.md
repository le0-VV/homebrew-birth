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

[Upstream PR #9](https://github.com/iAmCorey/birth/pull/9) includes a GitHub Actions workflow that updates this tap on stable releases. Once merged, publishing requires an upstream Actions secret named `HOMEBREW_TAP_TOKEN`: a fine-grained token with **Contents: read and write** access only to `le0-VV/homebrew-birth`. The workflow downloads the latest stable DMG, checks its SHA-256 against GitHub's asset digest, updates the cask, runs Homebrew style and online audit checks, and pushes only when the cask changes. Its manual **Run workflow** action retries the latest release if the DMG was uploaded after publication.

Until the upstream workflow is merged and configured, update `version` and `sha256` in `Casks/birth.rb` manually for each stable [upstream release](https://github.com/iAmCorey/birth/releases). Download the official DMG and calculate its checksum with `shasum -a 256` before committing.

Validate changes with:

```bash
brew style --cask le0-VV/birth/birth
brew audit --cask --strict --online le0-VV/birth/birth
brew fetch --cask le0-VV/birth/birth
```

Report application bugs [upstream](https://github.com/iAmCorey/birth/issues) and packaging issues [in this tap](https://github.com/le0-VV/homebrew-birth/issues).
