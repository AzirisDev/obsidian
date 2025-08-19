vimtutor is native little course on how to use vim. It usually takes up to 30 minutes to complete depending on how far you experiment. You will learn vim much faster if you run it and go through it everyday.

Commands:
- 1 - lesson - basics
	- :q! - quit vim WITHOUT save of changes
	- :wq - quit vim WITH save of changes
	- press x - to delete character under cursor, even in NORMAL mode
	- press a - to append, it text will start from the next character than cursor
- 2 - lesson - deletion
	- dw - delete the word from cursor till the start of next word
	- de - delete the word from cursor till the end of current word
	- d$ - delete from cursor till the end of this line
	- d is command for deletion, then motion command
	- [number] + w - start of next [number]th word, started from next word
	- [number] + e - end of the next [number]th word, started from current word
	- d + [number] + [motion] - deletes several words
	- dd - deletes entire line
	- u - undo ones
	- U - undo line
	- 0 - move to start of the line
	- $ - move to end of the line
- 3 - lesson - change operators
	- p - put info that was stored in vim register
	- r + [character] - replaces the character under cursor
	- ce - enters INSERT mode, and clears out characters until the end of the word
	- cc - does the same as [ce] but with whole line
	- c + [number] + [motion] - deletes several words and enters insert mode
- 4 - lesson - cursor location and file status
	- ctrl+G - shows location of a file
		- after that type G - go to the end 
		- after that type gg - got to the start
		- after that type [number of line] + G - go to certain line
	- / + phrase - search
		- n - to the top
		- N - to the bottom
	- ctrl + O - return the previous place
	- % - find matching parenthesis  
	- :s/old/new - change the first occurrence in line
	- :s/old/new/g - change all occurrences in line
	- :[number1],[number2]s/old/new/g - change all occurrences in between line numbers
	- :%s/old/new/g - change all occurrences in file
	- :%s/old/new/gc - change all occurrences in file with confirmation needed
- 5 - lesson - execute external command
	- :![command] - run any shell command
	- :!w [filename] - save current stuff inside file
	- :!rm [filename] - remove the file
	- v - opens visual selector
	- v + [select lines] + :w [filename] - save selected text to the file
	- :r + [filename] - reads content of file and puts under cursor
- 6 - lesson - commands
	- o - go INSERT mode, new line under cursor
	- O - go INSERT mode, new line above cursor
	- e - go to the end of each word in line
	- a - go INSERT mode, append from next character
	- A - go INSERT mode, append from the end of line
	- R - replace character by character in REPLACE mode
	- y - copy
		- yw - copy word
		- yy - copy line
	- p - paste
	- :set ic - ignore case
	- :set hls is -
		- hls - highlight search
		- is - is key word
		- :set nohls - remove highlight
- 7 - lesson - end
	- :help - help from native
	- vim scriptins - need to create vimrc files
	- ctrl + D + tab - command completion

Links:

202508190723

