We have three streams: 0 - stdin, 1 - stdout, 2 - stderr

#### Redirections
- > - output to file, overwrite if exists
- >> - output to file BUT append
- 2> - output to stderr stream, overwrites
- 2>> - output to stderr stream, appends
- &> - output to 1, 2 streams, overwrites
- &>> - output to 1, 2 streams, appends
- < - input from file
- << END - as long as input is reached to END
- <> - input from file and output to the same file

#### Pipes
- command1 | command2 - output from command1 will be input to command2
- xargs - get input as argument to use it further
- tee - run a command to see the output and also redirect it to the file

Links:

202509131511

