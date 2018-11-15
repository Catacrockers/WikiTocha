# Redirecting pipes

A pipeline is a sequence of processes chained together by their standard streams, so that the output of each process (stdout) feeds directly as input (stdin) to the next one.

## Redirect to files

Then, it is possible to redirect the output of a process (stdout) to a new file (overriding its content):

```
$ command > outputfile.txt  
```

It is possible to append stdout to a file at the bottom:

```
$ command >> outputfile.txt
```

If you want redirect the error messages of a process (stderr) as well use this:

```
$ command &> outputfile.txt   
```

To append it just:

```
$ command &>> outputfile.txt   
```

If you want to have both stderr and output displayed on the console and in a file use 'tee' command and pipe the output to it:

```
$ command | tee outputfile.txt
```

A slight modification will catch stderr as well:

```
$ command 2>&1 | tee outputfile.txt
```

or slightly shorter and less complicated:

```
$ command |& tee outputfile.txt
```

To summarize:

```
          || visible in terminal ||   visible in file   || existing
  Syntax  ||  StdOut  |  StdErr  ||  StdOut  |  StdErr  ||   file   
==========++==========+==========++==========+==========++===========
    >     ||    no    |   yes    ||   yes    |    no    || overwrite
    >>    ||    no    |   yes    ||   yes    |    no    ||  append
----------||----------|----------||----------|----------||----------
   2>     ||   yes    |    no    ||    no    |   yes    || overwrite
   2>>    ||   yes    |    no    ||    no    |   yes    ||  append
----------||----------|----------||----------|----------||----------
   &>     ||    no    |    no    ||   yes    |   yes    || overwrite
   &>>    ||    no    |    no    ||   yes    |   yes    ||  append
----------||----------|----------||----------|----------||----------
 | tee    ||   yes    |   yes    ||   yes    |    no    || overwrite
 | tee -a ||   yes    |   yes    ||   yes    |    no    ||  append
----------||----------|----------||----------|----------||----------
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    || overwrite
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    ||  append
----------||----------|----------||----------|----------||----------
|& tee    ||   yes    |   yes    ||   yes    |   yes    || overwrite
|& tee -a ||   yes    |   yes    ||   yes    |   yes    ||  append
----------||----------|----------||----------|----------||----------
```

* Please note that the n.e. in the syntax column means "not existing".
** There is a way, but it's too complicated to fit into the column. You can find a helpful link in the List section about it.

# Connections

To connect to a server though terminal you need to:

```
ssh $(user_name)@$(server_address)
```
