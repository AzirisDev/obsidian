It is a files that contains combined commands.
At the start of the file, we have shebang - tells the shell which interpreter to use.
Example: `#!/bin/bash` or `#!/bin/sh`

Scripts can get arguments and we can manage them via `$1`, `$2`, etc.

$(command)  OR `command` (back ticks)- output of any command will go there

#### Conditions
```
if [condition]
then
   do something
   do another thing
else
   do new things
   even funnier things
fi
```

| conditions  | what is means                                        |
| ----------- | ---------------------------------------------------- |
| "a" = "b"   | if two strings are equal (here it will return False) |
| "a" != "b"  | string a _is not equal_ to string b                  |
| 4 -lt 40    | if 4 is _lower than_ 40 (True)                       |
| 5 -gt 15    | if 5 is _greater than_ 15 (False)                    |
| 5 -ge 5     | if 5 is _greater or equal_ 5                         |
| 5 -le 3     | if 5 is _lower or equal_ to 3                        |
| 9 -ne 2     | 9 is _not equal_ with 2 (True)                       |
| -f FILENAME | if file FILENAME exists                              |
| -s FILENAME | if file exists and its size is more than 0 (Zero)    |
| -x FILENAME | if file exists and is executable                     |
#### Read
Reads user input
```
#!/bin/sh

echo "what is your name?"
read NAME

echo "Hello $NAME"

if [ $NAME = "Jadi" ]
then
    echo "Oh I know you!"
else
    echo "I wish I knew you"
fi
echo "Bye"
```

#### Loops
- For loops
```
for VAR in SOME_LIST;
do
  some stuff with $VAR
  some other stuff
done
```
- While loops
```
while [condition]
do
    do something
    do anohter thing
done
```

#### Mailing root user
Example 1:
```
jadi@funlife:~$ mail root
Cc:
Subject: Hi there root
hello there. This is my mail
```
Example 2:
```
echo "Body!" | mail -s "Subject" root
```


Links:
202509301902

