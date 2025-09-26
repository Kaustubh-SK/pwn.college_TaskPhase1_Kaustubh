# Digesting Documentation

## Learning From Documentation
We need to get the flag present in '_/challenge/challenge_' but it can't be accessed regularly. In order to get the flag we need to refer to the given documentation:

```Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!```

### Solve
**Flag:** `pwn.college{4zTHlnyh66aHrL0xnz0_TlUZhN9.QX0ITO0wyM0EzNzEzW}`

As written in the provided documentation I added the '_--giveflag_' argument while accessing the flag and got the flag.

```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4zTHlnyh66aHrL0xnz0_TlUZhN9.QX0ITO0wyM0EzNzEzW}
```

### New Learnings
Reading and getting help from documentations is a very important.

### References 
-NA-


## Learning Complex Usage
Using the given documentation we need to get the flag.
Here is this level's documentation for /challenge/challenge:

```Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!```

### Solve
**Flag:** `pwn.college{YATuuRdN-aBcVs3hLclAFku0md2.QX1ITO0wyM0EzNzEzW}`

As written in the provided documentation I gave path to the flag as the argument of the '_--printfile_' argument. I use the path '/flag' because it was previously mentioned that the flag is always inside '/flag' if not mentioned otherwise.

```bash
/challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{YATuuRdN-aBcVs3hLclAFku0md2.QX1ITO0wyM0EzNzEzW}
```

### New Learnings
Arguments themselves can have arguments.

### References 
-NA-


## Reading Manuals
This challenge makes us read the manual for '_challenge_' inorder to teach us the correct way to get he flag for this challeneg.

### Solve
**Flag:** `pwn.college{gRLjQkLWkfPAKUjDNAaLPOyfQca.QX0EDO0wyM0EzNzEzW}`

First I opened the manual for 'challenege' using '_man challenge_'. In the description it said "--gjkkfj NUM gives the flag if NUM is 000", so I did that and got the flag.

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --gjkkfj 000
Correct usage! Your flag: pwn.college{gRLjQkLWkfPAKUjDNAaLPOyfQca.QX0EDO0wyM0EzNzEzW}
```

### New Learnings
the '_man_' command gives out the manual of some different command given to it as an argument. These are very useful to learn the correct way to use a command. Press '**q**' to exit the manual.

### References 
-NA-


## Searching For Manuals
This challenge makes us search fot the manual that contains the information on how to print the flag.

### Solve
**Flag:** `pwn.college{IdjcL6jEfc4UYJ9IetG484X7Sge.QX2EDO0wyM0EzNzEzW}`

First I opened the manual for '_man_' there in the synopsis it was written on how to search for manuals. I couldn't completely understand what it all meant so I googled each flag's meaning seperately. Then after learning about them I used the '_-k_' flag to search the descritions of the manuals. And I searched for the word '**flag**' because it seemed the most logocal thing to search. The first man page that showed up had a random name and it's description was that it prints to the flag. So I opened that manual and got the argument to print the flag.

```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k flag
djcjfcetge (1)       - print the flag!
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/o...
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/o...
linux64 (1)          - change reported architecture in new program environment and/o...
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or ...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathco...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or...
setarch (1)          - change reported architecture in new program environment and/o...
setarch (8)          - change reported architecture in new program environment and/o...
x86_64 (8)           - change reported architecture in new program environment and/o...

hacker@man~searching-for-manuals:~$ man djcjfcetge
hacker@man~searching-for-manuals:~$ /challenge/challenge --djcjfc 649
Correct usage! Your flag: pwn.college{IdjcL6jEfc4UYJ9IetG484X7Sge.QX2EDO0wyM0EzNzEzW}
```

### New Learnings
There are several flags that can be used to do different things. The '_-k_' flag is used to search for a keyword in the description of manuals.

### References 
I googled the working of the different flags of the man command.


## Helpful Programs
Use the '_--help_' argument to get to the flag.

### Solve
**Flag:** `pwn.college{oMUlT5E0Og2R6nZldDV_6CcDwdV.QX3IDO0wyM0EzNzEzW}`

Since in the module the flag has been present in _/challenge/challenge_, I give it the '--help' argument. This shows the arguments I further need to give inorder to get to the flag. I use the '_-p_' to get the value to be put in the '_-g_' argument. This gives the flag.

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG]
                                            [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the
                        flag
hacker@man~helpful-programs:~$ /challenge/challenge --p
The secret value is: 502
hacker@man~helpful-programs:~$ /challenge/challenge --g 502
Correct usage! Your flag: pwn.college{oMUlT5E0Og2R6nZldDV_6CcDwdV.QX3IDO0wyM0EzNzEzW}
```

### New Learnings
The '_--help_' argument is useful to know the functioning of a command, especially if it doesn't have a _man_ page.

### References 
-NA-


## Help for Builtins
The '_challenge_' command has been made a builtin, using help we need to figure out a way to get to the flag.

### Solve
**Flag:** `pwn.college{c447IDx-QwtMKKBS9pR9ZelybPf.QX0ETO0wyM0EzNzEzW}`

Since _challenge_ is a builtin I invoke help and pass it _challenge_ through it, then I just get the flag by using the secret value and argument given in it.

```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "c447IDx-".
hacker@man~help-for-builtins:~$ challenge --secret c447IDx-
Correct! Here is your flag!
pwn.college{c447IDx-QwtMKKBS9pR9ZelybPf.QX0ETO0wyM0EzNzEzW}
```

### New Learnings
The shell has some built-in commands called '_builtins_' and the shell handles them internally. We can get help on a specific builtin by passing it through the _help_ builtin.

### References 
-NA-