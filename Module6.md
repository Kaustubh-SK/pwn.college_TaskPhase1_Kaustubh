# Practicing Piping

## Redirecting Output
In this challenge we need to redirect the word 'PWN' to the filename 'COLLEGE'.

### Solve
**Flag:** `pwn.college{McIb1oGmtxujQkmAvIIW928kSph.QX0YTN0wyM0EzNzEzW}`

I used the '>' character to redirect the output of _echo PWN_ to the file _COLLEGE_.

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{McIb1oGmtxujQkmAvIIW928kSph.QX0YTN0wyM0EzNzEzW}
```

### New Learnings
The '>' character is used to redirect the output of a command to another file. 

### References 
-NA-


## Redirecting more output
In this challenge we need to redirect the output of '_/challenge/run_'(which is the flag itself) into '_myflag_'. Then fetch the flag.

### Solve
**Flag:** `pwn.college{ws6ko4qBlB15EnwskhF8pahpZwT.QX1YTN0wyM0EzNzEzW}`

I used the '>' character to redirect the output of _/challenge/run_ to the file _myflag_. Then I read _myflag_ using _cat_.

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ws6ko4qBlB15EnwskhF8pahpZwT.QX1YTN0wyM0EzNzEzW}
```

### New Learnings
The instructions and feedback of a command are communicated over standard error but the output is communicated through standard out.

### References 
-NA-


## Appending Output
In this challenge we need to redirect the output of '_/challenge/run_'(which is the flag itself) into '_~/the-flag_' while using the append mode as the flag will be given in 2 parts. If append mode is not used the second half of the flag will overwrite the first half.

### Solve
**Flag:** `pwn.college{03L_FxBn3OihrN-FRDFmaer9Fne.QX3ATO0wyM0EzNzEzW}`

I used the '>>' character to redirect the output of _/challenge/run_ to the file _~/the-flag_ in append mode, this helps me prevent the overwriting of the first half of the flag.

```bash
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{03L_FxBn3OihrN-FRDFmaer9Fne.QX3ATO0wyM0EzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

### New Learnings
The '>>' character is used to redirect the output of a command to another file in append mode i.e. it aggregates the output of multiple commands if needed. Whereas '>' will overwrite the file everytime it is used. 

### References 
-NA-


## Redirecting errors
In this challenge we need to redirect the output of '_/challenge/run_'(which is the flag itself) into '_myflag_' and the 'errors'(which are instructions in our case) into '_instructions_'. Then get the flag.

### Solve
**Flag:** `pwn.college{sUWxJx1tDXpw6R3C6f1UySQOi8B.QX3YTN0wyM0EzNzEzW}`

I used the '>' character to redirect the standard output of _/challenge/run_ to the file _myfag_ and the errors to _instructions_ using '2>'. Then I _cat_ the flag.

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sUWxJx1tDXpw6R3C6f1UySQOi8B.QX3YTN0wyM0EzNzEzW}
```

### New Learnings
The '>' character can be prefixed with 0 or 1 or 2 to imply which channel we wish to redirect. 0 is for stdin, 1 is for stdout and 2 is for stderr.

### References 
-NA-


## Redirecting input
In this challenge '_/challenge/run_' needs us to redirect 'PWN' to it and 'PWN' must conatin the value 'COLLEGE'.

### Solve
**Flag:** `pwn.college{cvuQFci3Wpa-R5tXdoIOyviN47v.QXwcTN0wyM0EzNzEzW}`

First I redirected the output of _echo COLLEGE_ to PWN and then using the '<' character I redirected PWN to _/challenge/run_ and got the flag.

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cvuQFci3Wpa-R5tXdoIOyviN47v.QXwcTN0wyM0EzNzEzW}
```

### New Learnings
The '<' character is used to redirect input _to_ commands. 

### References 
-NA-


## Grepping stored results
In this challenge we need to redirect the output of '_/challenge/run_' into '_/tmp/data.txt_'. This will redirect hunder thousand lines of text with the flag being one of them, so we need to search for the flag as well.

### Solve
**Flag:** `pwn.college{EC4gMfnYZ89s2rDv8AOdmIvGR2Y.QX4EDO0wyM0EzNzEzW}`

First I redirected the output of _/challenge/run_ to _/tmp/data.txt_ and and then searched it using _grep_ and with the keyword _pwn.college_ because the flag always starts with that.

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{EC4gMfnYZ89s2rDv8AOdmIvGR2Y.QX4EDO0wyM0EzNzEzW}
```

### New Learnings
-NA- 

### References 
-NA-


## Grepping live output
In this challenge we need to redirect the output of '_/challenge/run_' into the standard input of _grep_ in order to directly find the flag.

### Solve
**Flag:** `pwn.college{UC-njm_RX7rngY3ROk-X4-tvabh.QX5EDO0wyM0EzNzEzW}`

I redirected the output of _/challenge/run_ to _grep_ by using '**|**'(called the _pipe_ operator) and gave the keyword _pwn.college_ because the flag always starts with that.

```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{UC-njm_RX7rngY3ROk-X4-tvabh.QX5EDO0wyM0EzNzEzW}
```

### New Learnings
We don't always need to store the redirected output of a command into a file. '|' is used to redirect the _stdout_ of a command to the _stdin_ of another command without needing to store anything.

### References 
-NA-


## Grepping errors
In this challenge we need to redirect the _stderr_ of '_/challenge/run_' into the _stdin_ of _grep_ in order to directly find the flag, but the '|' operator can only redirect _stdout_, so we need to use the '**>&**' operator which redirects a file descriptor to another file descriptor.

### Solve
**Flag:** `pwn.college{8cY9L_kT0UADfoO353_UW2VKeZS.QX1ATO0wyM0EzNzEzW}`

I redirected the _stderr_ of _/challenge/run_ to it's _stdout_ by using '2>& 1'(what this does is - it redirects fd2 to fd1, so the error gets redirected to the _stdout_ which can then be redirected to the _stdin_ of _grep_ using '|' ) and then I used '**|**' with _grep_ and gave the keyword _pwn.college_ because the flag always starts with that.

```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8cY9L_kT0UADfoO353_UW2VKeZS.QX1ATO0wyM0EzNzEzW}
```

### New Learnings
The '>&' operator is used to redirect a file descriptor to another file descriptor.

### References 
-NA-


## Filtering with grep -v
In this challenge we need to redirect the _stdout_ of '_/challenge/run_' into the _stdin_ of _grep_ in order to directly find the flag, but this time the output will have 1000 decoy flags that contain 'DECOY' somewhere in the flag. We need to filter them out and get the real flag.

### Solve
**Flag:** `pwn.college{kpDa7N9lHtgrcInvYjEgq4kiWHz.0FOxEzNxwyM0EzNzEzW}`

I redirected the output of _/challenge/run_ to _grep_ by using '**|**', but this time I used '_-v_' as an argument to _grep_ which will invert the filter i.e. it will only show me results that don't have the keyword in them and hence I gave the keyword 'DECOY' because all decoy flags have it somewhere within them. This gives the real flag as it doesn't contain the word 'DECOY' in it.

```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{kpDa7N9lHtgrcInvYjEgq4kiWHz.0FOxEzNxwyM0EzNzEzW}
```

### New Learnings
We can add '_-v_' argument to _grep_ to invert it's search filter.

### References 
-NA-


## Duplicating piped data with tee
In this challenge we need to pipe '_/challenge/pwn_' into '_/challenge/college_', but we need to intercept the data to see what _pwn_ needs to correctly pipe into _/challenge/college_.

### Solve
**Flag:** `pwn.college{YmXDOEqb1STfVavgqFZ2v82aeHd.QXxITO0wyM0EzNzEzW}`

I piped _/challenge/run_ into _tee pwnrequire_, this copies the _stdout_ of _/challenge/pwn_ to _pwnrequire_ and then writes the same to it's _stdout_ which is then piped to _/challenge/college_. Then we read _pwnrequire_ to find out the secret argument _pwn_ requires inorder to correctly pipe to _/challenge/college_. Then I just followed what the file said and got the flag.

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwnrequire | /cha
llenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwnrequire
Usage: /challenge/pwn --secret [SECRET_ARG]
SECRET_ARG should be "YmXDOEqb"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret YmXDOEqb | /ch
allenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{YmXDOEqb1STfVavgqFZ2v82aeHd.QXxITO0wyM0EzNzEzW}
```

### New Learnings
The '_tee_' command duplicates the data flowing thorugh the pipes to any number of files provided.

### References 
-NA-


## Process substitution for input
In this challenge we need to find the flag by finding what's diffrent between 2 files, i.e. decoys and decoys_and_flag. But instead of files we need to _diff_ two sets of commands: _/challenge/print\_decoys_ and _/challenge/print\_decoys\_and\_flag_. 

### Solve
**Flag:** `pwn.college{ENawqkOYqlGI-q0CHZdcfG8NEA5.0lNwMDOxwyM0EzNzEzW}`

I used '**<(command)**' to run those before-mentioned commands, this way bash runs them first and stores them in a temporary file and thus now _diff_ can be used to compare them and get the flag.

```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
11a12
> pwn.college{ENawqkOYqlGI-q0CHZdcfG8NEA5.0lNwMDOxwyM0EzNzEzW}
```

### New Learnings
'_<(command)_' makes bash run the command mentioned in it and store it's result in a temporary file that it creates. This is not a real file and is called a **Named Pipe**. This useful when we need to operate on things that are not files, such as commands, as we don't need to save everything into a new file.

### References 
-NA-


## Writing to multiple programs
In this challenge we need duplicate the output of _/challenge/hack_ as input into _/challenge/the_ and the _/challenge/planet_ commands.

### Solve
**Flag:** `pwn.college{oLuZpGkAhWrRcWZ-VKSxkpsehb6.QXwgDN1wyM0EzNzEzW}`

I used '_tee_' to duplicate the _stdout_ of _/challenge/hack_ and then write it as _stdin_ for the two commnads by using '**>(command)**', this excecutes the commnad with the output of _/challenge/hack_ as it's input and thus gives us the flag. Since we used '**()**', _tee_ thinks that these are files and not commnads.

```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
112002960180304573
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{oLuZpGkAhWrRcWZ-VKSxkpsehb6.QXwgDN1wyM0EzNzEzW}
```

### New Learnings
We can give give commands as input to other commands that require files as input by hiding them as files using '**>(command)**'. In this challenge the _tee_ commnad is supposed to write the output it recieves as input into 2 files, but these are actually commnads disguised as files and thus they take that as their input and get executed.

### References 
-NA-


## Split-piping stderr and stdout
In this challenge _/challenge/hack_ produces data on _stdout_ and _stderr_, we need to redirect the _stderr_ to _/challenge/the_ program and the _stdout_ to _/challenge/planet_ program.

### Solve
**Flag:** `pwn.college{EHGNL3t3xrXfAMQXe3Vsl_YYS_N.QXxQDM2wyM0EzNzEzW}`

It was mentioned before that '**| command**' and '**> >(command)**' mean the same thing, I used the second way as it is more flexible as I can prefix the first '>' with 2 to redirect the _stderr_ to any command. Thus I redirected the _stdout_ using '**> >(/challenge/planet)**' and the _stderr_ using '**2> >(/challenge/the)**'. This gives the flag.

I was not able to do it in the first try, but eventually I did get there when I refrenced the prvious challenges.

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2>
 >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{EHGNL3t3xrXfAMQXe3Vsl_YYS_N.QXxQDM2wyM0EzNzEzW}
```

### New Learnings
Sometimes using '**> >(command)**' can be more benificial than '**| command**', as '**|**' only redirects the _stdout_ and nothing else, whereas with '>' we can just prepend it with 0 or 1 or 2, according to our needs.

### References 
Previous challenges of this module especially 'Writing to multiple programs'.


## Named pipes
In this challenge we need to create a 'FIFO' file and redirect the _stdout_ of _/challenge/run_ to it, then the flag

### Solve
**Flag:** `pwn.college{sgbcsKXlrGsBwODDwEWz9scDnqk.01MzMDOxwyM0EzNzEzW}`

First I made the FIFO file using _mkfifo_ command and then redirect the _stdout_ of _/challenge/run_ to it. Because it's a FIFO file it gets **blocked** as this only opens the write side and inorder to open the read side I had to use another terminal, which was the WSL one that I connect to the PWN Dojo. Then I ran _cat /tmp/flag\_fifo_ in this second terminal and got the flag.

```bash
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!

hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{sgbcsKXlrGsBwODDwEWz9scDnqk.01MzMDOxwyM0EzNzEzW}
```

### New Learnings
We can create named pipes manully that actually persist in the file system unlike the named pipes that automatically get created during process susbtitution. Unlike regular files these don't store the data in them, when a FIFO file is read the data gets deleted because it is a _pipe_. FIFO files will **block** any operations on them until both the read side of the pipe and the write side of the pipe are ready.

### References 
I asked chatGPT how to connect my WSL terminal to the Dojo.