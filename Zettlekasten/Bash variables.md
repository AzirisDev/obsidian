- Do not leave space, bash will consider variable as command -> `name=DevOps`
- Single quotes -> literal string, Double quotes -> treats everything with variable expand
- Command substitution -> use `$(command)`
- Special arguments:
	- `$0` - first argument -> command/script itself
	- `$1, $2, ...` - arguments that are passed to the command/script
	- `$@` - all arguments
	- `$#` - number of arguments
	- `$?` - hold exit code of last command
- Environmental variables:
	- `export ENV_VAR=DevOps` - now you can access it from any child bash process

Links:

202608281829

