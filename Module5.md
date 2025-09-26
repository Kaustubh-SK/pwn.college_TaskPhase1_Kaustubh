# File Globbing

## Matching with *
In this challenge we need to change our directory to _/challenge_ but we can't give more than 4 characters as argument to _cd_, we must use '*'. Once in, we need to run _/challenge/run_ to get the flag.

### Solve
**Flag:** `pwn.college{gZbFQOBANPY93IjDirrVZWkOBF-.QXxIDO0wyM0EzNzEzW}`

I used '*' glob to shorten the path _/challenge_ to _/ch\*_, this limits the path to 4 characters(as required).

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /ch*/r*
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gZbFQOBANPY93IjDirrVZWkOBF-.QXxIDO0wyM0EzNzEzW}
```

### New Learnings
The '*' glob makes the shell find a directory or file that matches with the pattern before it, this shortens the paths.

### References 
Add any references or videos you used while solving the challenge.