# Shell Variables

## Printing Variables
In this challenge we need to print the variable **FLAG** using _echo_ to get the flag.

### Solve
**Flag:** `pwn.college{4dFNCikZV20-wFHVVqTp3kHFPe8.QX3UTN0wyM0EzNzEzW}`

I pepended the variable name with the '$' symbol so that _echo_ prints out the content in **FLAG**.

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{4dFNCikZV20-wFHVVqTp3kHFPe8.QX3UTN0wyM0EzNzEzW}
```

### New Learnings
1. Linux command line is a programming language and thus has variables.
2. There are many ways to print a variable and one of them is to use _echo_ but prepend the name of the variable with a '**$**' symbol.

### References 
-NA-


## Setting Variables
In this challenge we need to set the value of the 'PWN' variable to 'COLLEGE', this will give us the flag.

### Solve
**Flag:** `pwn.college{sFR_U3zMn7Vq-f9qjYUQ8kKhaEP.QX5UTN0wyM0EzNzEzW}`

I assigned the the value 'COLLEGE' to the variable 'PWN' using '**=**'. Also there is no space before or after '=', this is to prevent the shell thinking that it a command.

```bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sFR_U3zMn7Vq-f9qjYUQ8kKhaEP.QX5UTN0wyM0EzNzEzW}
```

### New Learnings
1. Variables are assigned values using '**=**'. 
2. There shouldn't be any spaces before or after the '='.
3. There is no need for the '$' symbol as it is only prepended to _access variables_.

### References 
-NA-


## Multi-word Variables
In this challenge we need to set the value of the 'PWN' variable to 'COLLEGE YEAH', this will give us the flag.

### Solve
**Flag:** `pwn.college{gY0J4NURWUFuk_aGeAyqh5xOklF.QXwYTN0wyM0EzNzEzW}`

I assigned the the value 'COLLEGE YEAH' to the variable 'PWN' using double quotes(""). This is to make sure the entireity of 'COLLEGE YEAH' is taken as single token and the space is not interpretted wrongly.

```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gY0J4NURWUFuk_aGeAyqh5xOklF.QXwYTN0wyM0EzNzEzW}
```

### New Learnings
1. In order to give multi word values to variables we need to use double quotes("") as space has a special meaning in the shell.

### References 
-NA-


## Exporting Variables
In this challenge we need to invoke _/challenge/run_ with the PWN variable with the value COLLEGE, and the COLLEGE variable set to the value PWN. The PWN variable must be exported and the COLLEGE variable must not be exported.

### Solve
**Flag:** `pwn.college{A3KY0TmeGnTHX3BOpSNkWdMHcPi.QXyYTN0wyM0EzNzEzW}`

I assigned the the value 'COLLEGE' to the variable 'PWN'  and exported it using _export_, both in the same line. This exported the variable _PWN_ that can now be used outside of the current shell process. Then I just normally assigned the value 'PWN' to the variable 'COLLEGE'. And finally I executed _/challenge/run_ with the variable _PWN_. I also tried it with _$PWN_, that also works.

```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run PWN
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{A3KY0TmeGnTHX3BOpSNkWdMHcPi.QXyYTN0wyM0EzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

### New Learnings
1. Variables created are local to that shell process and need to be exported to be used in a different shell process.

### References 
-NA-


## Printing Exported Variables
In this challenge we need to use the '_env_' command to print every exported variable set in our shell, and then find the flag among them.

### Solve
**Flag:** `pwn.college{w7XzpSnSoIY1KC1ETLL4rHLTw2O.QX4UTN0wyM0EzNzEzW}`

I just executed _env_ and all the exported variables were printed out, then I just looked for the flag and got it.

```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=0056bb95afd42bd8371e70a89d08d3d5699623866899f11ca8357bfe39940a47
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{w7XzpSnSoIY1KC1ETLL4rHLTw2O.QX4UTN0wyM0EzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

### New Learnings
1. The '_env_' command is used to print out every exported variable set in our shell.

### References 
-NA-


## Storing Command Output
In this challenge we need to read the output of _/challenge/run_ directly into a variable called _PWN_ using '**$()**', this will store the flag in it. Then we need to print it out.

### Solve
**Flag:** `pwn.college{YMaSF6PZN-9AJ2hm-MIOJl55ROf.QX1cDN1wyM0EzNzEzW}`

In order to assign the output of _/challenge/run_ to 'PWN' I ran it inside "**$()**"(as told in the challenge), and stored that inside PWN. Then to print the flag I used _ech0_ and prepended PWN with the dollar symbol.

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{YMaSF6PZN-9AJ2hm-MIOJl55ROf.QX1cDN1wyM0EzNzEzW}
```

### New Learnings
1. We can directly store the output of commands in variables by enclosing the command in '**$()**' and then assign it to the variable.

### References 
-NA-


## Reading Input
In this challenge we need to input the value of 'PWN' variable as 'COLLEGE' from the user usif=g the _read_ builtin.

### Solve
**Flag:** `pwn.college{4KSJ-4KzSAmhbGYtgdRVnpKodH3.QX4cTN0wyM0EzNzEzW}`

I used the _read_ command with '_-p_' argument to specify a prompt to enter the value of PWN. Then I entered 'COLLEGE' as the value to be stored in PWN and got the flag.

```bash
hacker@variables~reading-input:~$ read -p "Value of PWN: " PWN
Value of PWN: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4KSJ-4KzSAmhbGYtgdRVnpKodH3.QX4cTN0wyM0EzNzEzW}
```

### New Learnings
1. User input can be read using the '_read_' command.
2. We can also give it the '_-p_' argument to specify a prompt.

### References 
-NA-


## Reading Files
In this challenge we need to read the file _/challenge/read\_me_ into the variable _PWN_ in a single command to get the flag.

### Solve
**Flag:** `pwn.college{IROTR3XNO7PGUtJD0KF9YsxmhsH.QXwIDO0wyM0EzNzEzW}`

With the previous knowledge of redirecting _stdout_ and _stdin_, I redirect the the mentioned file into the _stdin_ of PWM using '<'. This gives me the flag

```bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IROTR3XNO7PGUtJD0KF9YsxmhsH.QXwIDO0wyM0EzNzEzW}
```

### New Learnings
1. Redirecting can be used to read values to variables.

### References 
-NA-