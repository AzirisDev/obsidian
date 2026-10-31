We are going to install mise with `chezmoiexternals`.

#### What is the problem? 
Imagine we have this `mise.toml` file where we list the tools that each dev container will have. But it can not contain your personal tools as you like cause it might a team container.

Also during creation of container we could have troubles with installing mise and our chezmoi will be blocked.

**Updating mise or a tool**: you have to rebuild the image instead of just running `chezmoi apply`.

**Separation of concerns**: the image should hold what the _project_ needs. Your shell, prompt, mise, and CLI tools are _yours_, and they belong in dotfiles.

#### Solution
`.chezmoiexternal.toml` tells chezmoi to download a file or archive from a URL and place it in your home directory as if it were part of your dotfiles. 


#### Steps
```
mkdir .chezmoiexternals
vi .chezmoiexternals/mise.toml


[".local/bin/mise"]
type = "file"
executable = true
url = "https://mise.jdx.dev/mise-latest-{{.chezmoi.os}}-{{.chezmoi.arch}}"
```

Here we are also downloading proper version and os type mise.

Now we should create config the install `OUR` tools:
```
mkdir -p dot_config/mise

vi dot_config/mise/config.toml

[tools]
bat = "latest"
chezmoi = "latest"

mkdir .chezmoiscripts
vi  .chezmoiscripts/run_onchange_after_install_packages.sh.tmpl


#!/bin/bash
# packages hash: {{ include "dot_config/mise/config.toml" | sha256sum }}
$HOME/.local/bin/mise trust $HOME/.config/mise/config.toml && $HOME/.local/bin/mise install
```

#### Chezmoiignore

Lets put here our `setup` file so that it is not also installing it into dev container workspace.


Links:

202610312041

