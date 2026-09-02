### What is UNIX filters and why do we need them?
UNIX filters gets input from `stdin`, writes output to `stdout` and do one thing.
`seq`, `grep`, `sort` - those are filters.

### Setup PATH to your place of filters to access it everywhere
- `mkdir -p ~/.local/bin`
- `echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc`
- `source ~/.bashrc`
Now put your every executable into `~/.local/bin`

Examples:
- Create `upper`:
```
#!/bin/bash
read -r line
echo "${line^^}"
```
- Create `lower`:
```
#!/bin/bash
read -r line
echo "${line,,}"
```
- gendate - Insert Today’s Date
```
#!/bin/bash
date +%Y-%m-%d
```

### Now the magic
In Vim you can run external commands using `!`.
`!!` runs the command to the current line. For example, if you do `!!upper` , you will uppercase the current line.
- `!!command`Filter current line
- `!}command`Filter to end of paragraph
- `!Gcommand`Filter to end of file
- `:'<,'>!command`Filter visual selection




Links:

202608291905

