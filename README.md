# dotfiles

Personal machine configuration for macOS (Apple Silicon).

## Setup

Clone and symlink:

```bash
git clone git@github.com:osubuu/dotfiles.git ~/dotfiles
ln -s ~/dotfiles/.zshrc ~/.zshrc
```

## Homebrew Packages

A `Brewfile` is included for one-command installs (`brew bundle --file=~/dotfiles/Brewfile`). It also captures VS Code extensions. The table below describes each package — keep both in sync when adding or removing packages. To regenerate the Brewfile: `brew bundle dump --file=~/dotfiles/Brewfile --force`.

| Package | Purpose |
|---|---|
| `bun` | TypeScript/JavaScript runtime and bundler (via `oven-sh/bun` tap) |
| `gh` | GitHub CLI |
| `node` | Node.js runtime (brings npm) |
| `pnpm` | JavaScript/TypeScript package manager |
| `python3` | Python runtime (installs latest stable, shadows Xcode-bundled 3.9) |
| `uv` | Python package manager |
| `zsh` | Shell (newer than macOS bundled version) |
| `jq` | JSON processor (used in shell scripting) |
| `fzf` | Fuzzy finder — shell history search via `ctrl+r` |
| `git-delta` | Better git diffs — syntax highlighting, side-by-side view |
| `ripgrep` | Fast code search across files |
| `tlrc` | Simplified man pages (`tldr <command>`) |

## Shell

- **Shell:** zsh via oh-my-zsh
- **Theme:** robbyrussell
- **fzf integration:** enabled via `eval "$(fzf --zsh)"` in `.zshrc`
- **Plugins:** `git`, `zsh-autosuggestions`, `zsh-syntax-highlighting`

The two custom plugins must be cloned into `~/.oh-my-zsh/custom/plugins/`:

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
```

## Git

The actual `~/.gitconfig` is not tracked because it contains PII (name, email). A template is provided at `.gitconfig.example` — copy it and fill in your details:

```bash
cp ~/dotfiles/.gitconfig.example ~/.gitconfig
```

## Package Manager Conventions

- **JavaScript/TypeScript:** `pnpm` only — never `npm install` or `yarn`
- **Python:** `uv` only — never `pip` or `pip3` to install packages
- **Global npm packages:** none — use `pnpm dlx` for one-off CLI tools
- **Global uv tools:** none — use `uv run` or per-project `uv add`

## Notes

- `pip3` and system Ruby `gem` are present as macOS/Xcode bundled tools — ignored, not used for development
- `npm` is present but not used — it is bundled with `node` and cannot be removed independently
- `/usr/bin/python3` (Xcode-bundled 3.9.6) still exists but is shadowed by Homebrew's `python3` in PATH
