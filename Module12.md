# Chaining Commands

## Chaning with Semicolons
In this challenge we need to run _/challenge/pwn_ and then _/challenge/college_ by chaining them together using a semicolon.

### Solve
**Flag:** `pwn.college{QlVqXEcK1CPQGix6W7PkqKPb0Fg.QX1UDO0wyM0EzNzEzW}`

I typed _/ch*/pwn_ then put a smeicolon to chain the next command which was _/ch*/college_, this does what was asked in the question and gives us the flag.

```bash
hacker@chaining~chaining-with-semicolons:~$ /ch*/pwn;/ch*/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{QlVqXEcK1CPQGix6W7PkqKPb0Fg.QX1UDO0wyM0EzNzEzW}
```

### New Learnings
1. A _semicolon_(;) is used to chain multiple commands together.
2. It works in a very similar way to how pressing enter between 2 commands works.

### References 
-NA-


## Building on Success
In this challenge we need to chain _/challenge/first-success_ and _/challenge/second_ using the '**&&**' operator. But first we need to try and run them seperately and then chain them together to get the flag.

### Solve
**Flag:** `pwn.college{Iuyj-qfBRPDkww-FQTYJhkXpW5d.0lM0MDOxwyM0EzNzEzW}`

First I ran _/challenge/first-success_ and _/challenge/second_ indivudually and nothing happend. Then I chained them together using '**&&**' and that's when I get the flag.

```bash
hacker@chaining~building-on-success:~$ /ch*/first-success
hacker@chaining~building-on-success:~$ /ch*/second
Error: /challenge/first-success must be successfully chained with 
/challenge/second using &&
hacker@chaining~building-on-success:~$ /ch*/first-success && /ch*/second
Nice chaining! Flag: pwn.college{Iuyj-qfBRPDkww-FQTYJhkXpW5d.0lM0MDOxwyM0EzNzEzW}
```

### New Learnings
1. The _AND_(**&&**) operator allows us to execute the second command only if the first command succeeds, which basically means that the second command runs if the first command exited with the code 0.
2. It means: Run command1, and IF it succeeds, then run command2

### References 
-NA-


## Handling Failure
In this challenge we need to chain _/challenge/first-failure_ and _/challenge/second_ using the '**||**' operator to get the flag.

### Solve
**Flag:** `pwn.college{wWXFZGr_x5pLWnJSLkohJWXVr9B.01M0MDOxwyM0EzNzEzW}`

I chained _/ch*/first-failure_ and _/ch*/second_ together using '**||**' and this gives me the flag.

```bash
hacker@chaining~handling-failure:~$ /ch*/first-failure || /ch*/second
Nice chaining! Flag: pwn.college{wWXFZGr_x5pLWnJSLkohJWXVr9B.01M0MDOxwyM0EzNzEzW}
```

### New Learnings
1. The _OR_(**||**) operator allows us to execute the second command only if the first command fails, which basically means that the second command runs if the first command exited with a non-zero code.
2. It means: Run command1, and IF it fails, then run command2

### References 
-NA-


## Your First Shell Script
In this challenge we need to run _/challenge/pwn_ and then _/challenge/college_, but this time in a shell script called '**x.sh**'. Then we have to run it using _bash_ to get the flag.

### Solve
**Flag:** `pwn.college{415ZhWf3LcBpFMHmdfXhejLTaEH.QXxcDO0wyM0EzNzEzW}`

First I changed the mode to desktop on the pwn.college website, there I went into the text editor and created a '**x.sh**' file with first line being _/challenge/pwn_ and the second being _/challenge/college_. Then I switched back to the terminal and ran the script using _bash_ and this gave me the flag.

```bash
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{415ZhWf3LcBpFMHmdfXhejLTaEH.QXxcDO0wyM0EzNzEzW}
```

### New Learnings
1. We can put multiple commands in a file (called a shell script) and then execute them by executing the file using _bash_.

### References 
-NA-


## Redirecting Script Output
In this challenge we need to create a script that calls _/challenge/pwn_ and then _/challenge/college_ and then pipe the output of that script into a _/challenge/solve_.

### Solve
**Flag:** `pwn.college{gJ0XMuyb2VGdby8-hXMzIRHETbw.QX4ETO0wyM0EzNzEzW}`

Since I already created the '**x.sh**' script I executed it using _bash_ and piped it's output into _/challenge/solve_, this gave me the flag.

```bash
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{gJ0XMuyb2VGdby8-hXMzIRHETbw.QX4ETO0wyM0EzNzEzW}
```

### New Learnings
1. We can pipe/redirect outputs of script files into commnads

### References 
-NA-


## Executable Shell Scripts
In this challenge we need to create a script that invokes _/challenge/solve_, we also have to make it executable and then run it without explicitly invoking _bash_.

### Solve
**Flag:** `pwn.college{oHJlsX3UqYEt3-aad6iZaVRDYq7.QX0cjM1wyM0EzNzEzW}`

I created a new script file called '**execScript.sh**' using the desktop mode and then shifted back to the terminal. In the terminal I first check the script's permissions, since we don't have the execution rights I use _chmod_ with the '**a+x**' argument for the script file which gives execution rights to everyone. Then I execute the file and get the flag.

```bash
hacker@chaining~executable-shell-scripts:~$ ls -l execScript.sh
-rw-r--r-- 1 hacker hacker 17 Sep 30 17:27 execScript.sh
hacker@chaining~executable-shell-scripts:~$ chmod a+x execScript.sh
hacker@chaining~executable-shell-scripts:~$ ./execScript.sh
Congratulations on your shell script execution! Your flag:
pwn.college{oHJlsX3UqYEt3-aad6iZaVRDYq7.QX0cjM1wyM0EzNzEzW}
```

### New Learnings
1. We run script files without explicitly using _bash_ by giving them execution permission.

### References 
-NA-


## Understanding Shebangs
In this challenge we need to create a script called '**solve.sh**' that has a proper shebang and outputs 'hack the planet', we also have to make it executable and then run _/challenge/run_ to verify our script.

### Solve
**Flag:** `pwn.college{UX8v4srq-48iY1gvUkrCA7aIss8.0VOzMDOxwyM0EzNzEzW}`

I created a new script file called '**solve.sh**' using the desktop mode, with the first line being "**#!/bin/bash**" and the second line '_echo "hack the planet"_'. Then I shifted back to the terminal, in the terminal I first check the script's permissions, since we don't have the execution rights I use _chmod_ with the '**a+x**' argument for the script file which gives execution rights to everyone. Then I run _/cha*/run_ which checks my script and returns me the flag.

```bash
hacker@chaining~understanding-shebangs:~$ ls -l solve.sh
-rw-r--r-- 1 hacker hacker 35 Sep 30 17:38 solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x solve.sh
hacker@chaining~understanding-shebangs:~$ /ch*/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{UX8v4srq-48iY1gvUkrCA7aIss8.0VOzMDOxwyM0EzNzEzW}
```

### New Learnings
1. If a program file stars with '**#!**' we call it a '**shebang**', linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter.
2. '_#!/bin/bash_' is the interpreter for shell scripts.

### References 
-NA-


## Scripting with Arguments
In this challenge we need to write to '**solve.sh**' script that takes two arguments and outputs them in reverse order.Then once the script works we need to run _/challenge/run_ to verify our script and get the flag.

### Solve
**Flag:** `pwn.college{8OP1wpeaEAAt65o167NuqXTjpji.0VNzMDOxwyM0EzNzEzW}`

I edited the '**solve.sh**' script file using the desktop mode, with the first line still being "**#!/bin/bash**" but I change the second line to '_echo "$2 $1"_', this basically means that the second argument taken will be printed in place of '$2' and the first argument will be printed inplace of '$1'. Then I run the script to check my script and then I run _/ch*/run_ to get the flag.

```bash
SCRIPT:

#!/bin/bash
echo "$2 $1"
```

```bash
hacker@chaining~scripting-with-arguments:~$ ./solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /ch*/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{8OP1wpeaEAAt65o167NuqXTjpji.0VNzMDOxwyM0EzNzEzW}
```

### New Learnings
1. While excuting script files we can give them arguments.
2. Inside the shell script we use placeholders i.e. $1,$2,$3, etc. for the first, second, third arguments and so on.

### References 
-NA-


## Scripting with Conditionals
In this challenge we need to write to '**solve.sh**' script that outputs 'college' if the argument is 'pwn' and outputs nothing if the argument is anything else. Then once the script works we need to run _/challenge/run_ to verify our script and get the flag.

### Solve
**Flag:** `pwn.college{Eo7x2Vmf28MrJR0LA5YH-In6qgP.0lNzMDOxwyM0EzNzEzW}`

I edited the '**solve.sh**' script file using the desktop mode, with the first line still being "**#!/bin/bash**" but I changed the next few lines to the '**if**' conditional that checks if the first argument is 'pwn' it outputs 'college' and does nothing for anything else. Then I run the script to check my script and then I run _/ch*/run_ to get the flag.

```bash
SCRIPT:

#!/bin/bash
if [ $1 = 'pwn' ]
then
    echo college
fi
```

```bash
hacker@chaining~scripting-with-conditionals:~$ ./solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ ./solve.sh flag
hacker@chaining~scripting-with-conditionals:~$ /ch*/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{Eo7x2Vmf28MrJR0LA5YH-In6qgP.0lNzMDOxwyM0EzNzEzW}
```

### New Learnings
1. We can have '**if**' conditional in shell scripts.
2. The syntax is very strict, there must be a space after _if_, after '[' and before ']'.
3. _if_, _then_, and _fi_ must all be on different lines or separated by semicolons.
4. In order to terminate _if_ we must use _fi_.

### References 
-NA-


## Scripting with Default Cases
In this challenge we need to write to '**solve.sh**' script that outputs 'college' if the argument is 'pwn' and 'nope' if the argument is anything else. Then once the script works we need to run _/challenge/run_ to verify our script and get the flag.

### Solve
**Flag:** `pwn.college{o1YokCSDrjeGiCZmLNZevKmKxT_.01NzMDOxwyM0EzNzEzW}`

I edited the '**solve.sh**' script file using the desktop mode, with the first line still being "**#!/bin/bash**" but I added the '**else**' clause to the prvious '**if**' conditional. Then I run the script to check my script and then I run _/ch*/run_ to get the flag.

```bash
SCRIPT:

#!/bin/bash
if [ $1 = 'pwn' ]
then
    echo college
else
    echo nope
fi
```

```bash
hacker@chaining~scripting-with-default-cases:~$ ./solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ ./solve.sh flag
nope
hacker@chaining~scripting-with-default-cases:~$ /ch*/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{o1YokCSDrjeGiCZmLNZevKmKxT_.01NzMDOxwyM0EzNzEzW}
```

### New Learnings
1. The '**if**' conditional can have an '**else**' clause that only runs when the condition in _if_ fails.
2. Using _else_ is optional and it doesn't have a _then_ statement.

### References 
-NA-


## Scripting with Multiple Conditions
In this challenge we need to write to '**solve.sh**' script that outputs 'college' if the argument is 'pwn', 'the planet if the argument is 'hack', 'linux' if the argument is 'learn' and 'unknwon' if the argument is anything else. Then once the script works we need to run _/challenge/run_ to verify our script and get the flag.

### Solve
**Flag:** `pwn.college{Ihff1D3QKQF3Nt_sPw-lvYnpoiW.0FOzMDOxwyM0EzNzEzW}`

I edited the '**solve.sh**' script file (using the desktop mode) as given below. Then I run the script to check my script and then I run _/ch*/run_ to get the flag.

```bash
SCRIPT:

#!/bin/bash
if [ $1 == "pwn" ]
then
    echo college
elif [ $1 == "hack" ]
then
    echo "the planet"
elif [ $1 == "learn" ]
then
    echo linux
else
    echo "unknown"
fi
```

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ ./solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ ./solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ ./solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ ./solve.sh flag
unknown
hacker@chaining~scripting-with-multiple-conditions:~$ /ch*/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{Ihff1D3QKQF3Nt_sPw-lvYnpoiW.0FOzMDOxwyM0EzNzEzW}
```

### New Learnings
1. The '**if**' conditional can have an '**elif**' clauses that have their own conditions.
2. Using _elif_ is optional and but they require a _then_ statement.

### References 
-NA-


## Reading Shell Scripts
In this challenge we need to read the _/challenge/run_ shell script and figure out the password it requires in order for it to give us the flag.

### Solve
**Flag:** `pwn.college{8MBu6lMHsB6wOy-vQEDwbJEigBN.0lMwgDOxwyM0EzNzEzW}`

I read the _/challenge/run_ shell script using _cat_, there I could see that the for it to give us the flag we must enter the password 'hack the PLANET'. Thus I use it and get the flag.

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /ch*/run
hack the PLANET
CORRECT! Your flag:
pwn.college{8MBu6lMHsB6wOy-vQEDwbJEigBN.0lMwgDOxwyM0EzNzEzW}
```

### New Learnings
1. Shell scripts can be read using _cat_.

### References 
-NA-