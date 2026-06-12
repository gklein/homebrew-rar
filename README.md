# Homebrew Tap for UnRAR

Homebrew formula for installing [`unrar`](https://www.rarlab.com/) — the official
RARLAB command-line tool to extract, view, and test RAR archives — on macOS and Linux.

## Install

`unrar` lives in a third-party (non-official) tap. Recent Homebrew versions
ask you to explicitly **trust** a tap before installing from it by short name,
since tapping loads the formula's Ruby code from this repository.

### Quick install (fully-qualified name)

```sh
brew install gklein/rar/unrar
```

### Tap, trust, then install

```sh
brew tap gklein/rar
brew trust --formula gklein/rar/unrar
brew install unrar
```

`brew trust --formula …` trusts only the `unrar` formula, which is the
recommended approach. If you'd rather trust everything in this tap — now and in
the future — you can trust the whole tap instead:

```sh
brew trust gklein/rar
```

You can review or revoke trust at any time:

```sh
brew trust                 # list trusted entries
brew untrust gklein/rar    # stop trusting
```

> **Note:** Explicit tap trust becomes mandatory in Homebrew 5.2.0 / 6.0.0
> (whichever lands first). To opt in early and verify these steps work, set
> `HOMEBREW_REQUIRE_TAP_TRUST=1`.

## Upgrade

```sh
brew upgrade unrar
```

## Usage

```sh
unrar x archive.rar    # extract with full paths
unrar e archive.rar    # extract to the current directory
unrar l archive.rar    # list archive contents
unrar t archive.rar    # test archive integrity
```

## License

`unrar` is distributed under the **UnRAR license**, which permits extracting RAR
archives but forbids using the source to recreate the RAR compression algorithm.
Installing this formula agrees to that license on your behalf; the full text is
installed at `$(brew --prefix)/opt/unrar/license.txt`. If those terms are
unacceptable, uninstall the formula.

## How it works

This tap builds `unrar` from the official source tarball published at
[rarlab.com](https://www.rarlab.com/rar_add.htm) and installs both the `unrar`
binary and the `libunrar` shared library. A daily GitHub Actions workflow checks
RARLAB for new releases and updates the formula automatically when one ships.
