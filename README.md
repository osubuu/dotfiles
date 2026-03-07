# dotfiles

Personal machine configuration for macOS (Apple Silicon).

## Setup

Clone and symlink:

```bash
git clone git@github.com:osubuu/dotfiles.git ~/dotfiles
ln -s ~/dotfiles/.zshrc ~/.zshrc
```

## Homebrew Packages

| Package | Purpose |
|---|---|
| `gh` | GitHub CLI |
| `node` | Node.js runtime (brings npm) |
| `pnpm` | JavaScript/TypeScript package manager |
| `uv` | Python package manager |
| `zsh` | Shell (newer than macOS bundled version) |
| `jq` | JSON processor (used in shell scripting) |
| `fzf` | Fuzzy finder — shell history search via `ctrl+r` |
| `ripgrep` | Fast code search across files |

## Shell

- **Shell:** zsh via oh-my-zsh
- **Theme:** robbyrussell
- **fzf integration:** enabled via `eval "$(fzf --zsh)"` in `.zshrc`

## Package Manager Conventions

- **JavaScript/TypeScript:** `pnpm` only — never `npm install` or `yarn`
- **Python:** `uv` only — never `pip` or `pip3` to install packages
- **Global npm packages:** none — use `pnpm dlx` for one-off CLI tools
- **Global uv tools:** none — use `uv run` or per-project `uv add`

## Notes

- `pip3` and system Ruby `gem` are present as macOS/Xcode bundled tools — ignored, not used for development
- `npm` is present but not used — it is bundled with `node` and cannot be removed independently
