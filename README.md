# tothlp's dotfiles
:seedling: dotfiles, managed by chezmoi. :house:

This repo holds some configuration files for my current setup, which are managed by chezmoi across multiple workstations.

## :wrench: Installation

First of all, we need to install *git*, which is packed in Xcode command line tools.

```bash
sudo softwareupdate -i -a
xcode-select --install
```

Next, we will need Homebrew. The installation below is copied from the Homebrew official site.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install chezmoi, and init it from this repo.

```bash
brew install chezmoi
```

```bash
chezmoi init --apply tothlp
```

Apply the config files

```bash
chezmoi -v apply
```

At last, install the packages from Brewfile.

```bash
brew bundle
```
