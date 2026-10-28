Pronounced sheymwa, tool for managing your personal dotfiles and more.
Templates, running scripts, file encryption, importing files from archives. 

https://www.chezmoi.io

You can check operating system or hostname and then do conditional setups.

#### Quickstart
Roughly speaking, chezmoi stores the desired state of your dotfiles in the directory `~/.local/share/chezmoi`. It calculates minimal changes required for our dotfiles to match our desired state.

- `chezmoi init` - creates this share directory
- `chezmoi diff` - shows what is different from real and desired state
- `chezmoi apply` - apply the changes

Minimal setup script for chezmoi:
```
#!/bin/bash

set -euo pipefail

if ! command -v chezmoi >/dev/null; then
    sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply git@github.com:AzirisDev/dotfiles.git
fi

exit 0
```

Links:

202610281704

