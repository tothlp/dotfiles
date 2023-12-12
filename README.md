# tothlp's dotfiles
:seedling: dotfiles, managed by chezmoi. :house:

This repo holds some configuration files for my current setup, which are managed by chezmoi across multiple workstations and Codespaces.

## :wrench: Automated Installation

Install chezmoi first, and pull configs from this repo.

```bash
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply tothlp
```

Apply the configs. Note, that before applying the configs, it will run the init scripts located in .chezmoiscripts folder. It will install Xcode command line tools, and homebrew for us. Afterwards, chezmois applies the configs.

```bash
chezmois apply
```

After applying the configs, the [.chezmoiscripts/run_once_after_00_install-packages-from-brewfile.sh.tmpl](.chezmoiscripts/run_once_after_00_install-packages-from-brewfile.sh.tmpl) script runs `brew bundle`, and installs dependencies from `Brewfile`.

## :wrench: Manual Installation

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

## :sunny: Day-to-day usage

Recreate Brewfile if needed

```bash
brew bundle dump --force
```

Add it to chezmoi, so Git can notice changes

```bash
chezmoi add Brewfile
```

We can also edit the chezmoi-managed files directly

```bash
chezmoi edit ~/.zshrc
```

See the diff, apply changes

```bash
chezmoi diff
chezmoi apply -v
```

After that, we can change into chezmoi's directory, and review changes, push to git, etc

```bash
chezmoi cd
```

## Additional resources

[Official chezmoi repository](https://github.com/twpayne/chezmoi)

[chezmoi site](https://www.chezmoi.io)


