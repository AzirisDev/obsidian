I was wrong. Shell is NOT “a place to type commands”.
Turns out, it is an entire ecosystem that decides how everything runs.

This week I dug into how shells actually work, and a few things surprised me.

Surprises:
1. You can check your current shell using echo $0 or echo $SHELL.
2. Before executing anything, the shell checks if a command is internal or external. If it is external, PATH decides where to find the executable.
3. Useful commands I wish I knew earlier: `type` shows internal or external, `which` shows the path, `whatis` shows a description, `whereis` locates files, `uname` gives system info, and escaping is done with a backslash.
4. Shells come in login and interactive modes, non login interactive modes, and non interactive modes.
5. Environment variables control how the system behaves. Variables like HOME, PATH, PS1, and HISTFILE all shape your experience.
6. Using source script.sh runs a script without creating a new shell, something that suddenly made many tutorials make sense.

Learning these fundamentals made the shell feel much less mysterious.

What shell concepts confused you at first and suddenly made sense later? I would love to learn from your experience 👇

#Linux #Shell #DevOps #Productivity #EngineeringBasics

![[Gemini_Generated_Image_5j5bt85j5bt85j5b.png]]