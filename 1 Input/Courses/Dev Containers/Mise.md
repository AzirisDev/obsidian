https://mise.jdx.dev

Mise-en-place, pronounced `meez` en place.
mise installs a project's tools, sets its environment variables, and runs its tasks from one `mise.toml` that works in your shell, editor, and CI. With `mise bootstrap`, it can also set up a whole machine: packages, dotfiles, and services.


#### Quickstart
- `mise doctor` - shows problems with mise
- `mise help activate`
- `eval "$(mise activate bash)"` - we need to add it to our [[Chezmoi]] `bashrc`, to activate mise
- `mise use chezmoi` - install package/tool and creates/adds it to `toml` file
- `mise registry` - shows all tools available to be downloaded

#### Mise trust
Mise activates automatically when we get into the directory with `mise.toml`. We should trust workspace with mise as a additional layer of security. So we can add this to the dev container setup:
- `"postCreateCommand": "mise trust && mise install"`

`mise trust --show` - show which places are trusted

Links:

202610291619

