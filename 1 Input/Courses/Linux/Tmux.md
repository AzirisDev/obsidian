### What is tmux and why do we need it?

`Tmux` - terminal multiplier.
It gives following opportunities:
- `Session persistency` - disconnect and connect without losing work, until machine is on
- `Multiple panes` - split terminal
- `Multiple window` - create windows/tabs

### Key bindings

Main key binding: `Ctrl + b`

- `Ctrl + b + d` - detach; exit tmux, but tmux is still running
- `tmux ls` - shows running tmuxes
- `tmux attach` - enter latest tmux
	- `tmux attach -t 0/name` - enter certain tmux
- `tmux` - create tmux
	- `tmux new -s name` - create tmux with name
- `tmux kill-session -t 0/name` - kills tmux

### Control inside tmux

#### Windows
- Create new window`Ctrl+b c`
- Next window`Ctrl+b n`
- Previous window`Ctrl+b p`
- Window by number`Ctrl+b 0-9`
- Rename window`Ctrl+b ,`
- Close windowType `exit` or `Ctrl+b &`

#### Panes
- Split horizontal`Ctrl+b "`
- Split vertical`Ctrl+b %`
- Move between panes`Ctrl+b arrow`
- Close paneType `exit` or `Ctrl+b x`
- Toggle full-screen`Ctrl+b z`
- Resize pane`Ctrl+b Ctrl+arrow`
  

Links:

202608241438

