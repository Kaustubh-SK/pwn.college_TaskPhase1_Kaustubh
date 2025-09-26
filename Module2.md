# Pondering Paths

## The Root
We need to invoke the _pwn_ program using it's absolute path to get the flag.

### Solve
**Flag:** `pwn.college{0fN3ZeLvhna8gaWQA8-FBI_Ud6Z.QX4cTO0wyM0EzNzEzW}`

I typed _/pwn_ and pressed enter.

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0fN3ZeLvhna8gaWQA8-FBI_Ud6Z.QX4cTO0wyM0EzNzEzW}
```

### New Learnings
The file system of linus starts at "/", it can consist of multiple directories and files.

### References 
-NA-


## Program and absolute paths
In this challenge we need to execute the program "*run*" under the _challenge_ directory using it's absolute path.

### Solve
**Flag:** `pwn.college{k1jjZOc0k_sotaicKRBrSfChnQJ.QX1QTN0wyM0EzNzEzW}`

I typed _/challenge/run_ and pressed enter

```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{k1jjZOc0k_sotaicKRBrSfChnQJ.QX1QTN0wyM0EzNzEzW}
```

### New Learnings
We can execute a program directly using it's absolute path.

### References 
-NA-


## Position thy self
We again need to execute "*run*" using it's absolute path but from a different specified directory/path.

### Solve
**Flag:** `{8kDc7cDtiYrWfdcROEWehUZyuCZ.QX2QTN0wyM0EzNzEzW}`

I typed _/challenge/run_ and pressed enter to get the correct directory where I need to go in order to execute _run_. Then I used "***cd***" to get to that directory and executed _run_.

```bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var/lib/apt/lists
hacker@paths~position-thy-self:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8kDc7cDtiYrWfdcROEWehUZyuCZ.QX2QTN0wyM0EzNzEzW}
```

### New Learnings
The _cd_ command is used to navigate the filesystem in linux.

### References 
-NA-


## Position elsewhere
We again need to execute "*run*" using it's absolute path but from a different specified directory/path.

### Solve
**Flag:** `pwn.college{EVgfnoozmhntXo0QcryILeQ55SZ.QX3QTN0wyM0EzNzEzW}`

I typed _/challenge/run_ and pressed enter to get the correct directory where I need to go in order to execute _run_. Then I used "***cd***" to get to that directory and executed _run_.

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EVgfnoozmhntXo0QcryILeQ55SZ.QX3QTN0wyM0EzNzEzW}
```

### New Learnings
-NA-

### References 
-NA-


## Position yet elsewhere
We again need to execute "*run*" using it's absolute path but from a different specified directory/path.

### Solve
**Flag:** `pwn.college{kMEQMLXL0eRUkxhDw5FnWyxYDBw.QX4QTN0wyM0EzNzEzW}`

I typed _/challenge/run_ and pressed enter to get the correct directory where I need to go in order to execute _run_. Then I used "***cd***" to get to that directory and executed _run_.

```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/include
hacker@paths~position-yet-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{kMEQMLXL0eRUkxhDw5FnWyxYDBw.QX4QTN0wyM0EzNzEzW}
```

### New Learnings
-NA-

### References 
-NA-


## Implicit relative paths, from /
We need to execute "*run*" using it's relative path while '/' is the current directory.

### Solve
**Flag:** `pwn.college{kd7gKBiQG3ecfHfjcL6sIpk6fyZ.QX5QTN0wyM0EzNzEzW}`

First I went in the root directory i.e.'/' using _cd_ and then executed the "_run_" program using it's relative path.

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{kd7gKBiQG3ecfHfjcL6sIpk6fyZ.QX5QTN0wyM0EzNzEzW}
```

### New Learnings
There two types of paths, absolute and relative. A relative path is interpretd only in the context on the current working directory(cwd). Also '**..**' refers to the parent directory.

### References 
-NA-


## Explicit relative paths, from /
This challenge makes us use '**.**' in relative paths.

### Solve
**Flag:** `pwn.college{I0KOhkTb-E4iSPlYMsaP7OGJucM.QXwUTN0wyM0EzNzEzW}

First I went in the root directory i.e."/" using _cd_ and then executed the "_run_" program using it's relative path but this time also incorporating '**.**' in the relative path. I used it at the start.

```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{I0KOhkTb-E4iSPlYMsaP7OGJucM.QXwUTN0wyM0EzNzEzW}
```

### New Learnings
'**.**' refers to the same directory for both absolute and relative paths.

### References 
-NA-


## Implicit relative paths
This challenge makes us use '**.**' to execute '_run_' within the challenge directory.

### Solve
**Flag:** `pwn.college{0KuqR93R7FGOJLsfDKp1gZOQ5xT.QXxUTN0wyM0EzNzEzW}`

First I went in the challenge directory i.e."/challenge" using _cd_ and then executed the "_run_" program using the relative path but with '**./**' at the start to ensure it's still a relative path. Just using '**.**' will not work.

```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ .run
bash: .run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0KuqR93R7FGOJLsfDKp1gZOQ5xT.QXxUTN0wyM0EzNzEzW}
```

### New Learnings
We use '**./**' to execute a program within a directory.

### References 
-NA-


## Home sweet home
We need to give an absolute path for a place in the home directory as an argument to the "_/challenge/run_" command. The argument must be 3 characters or less. This copies the flag to our specified path and returns it back to us.

### Solve
**Flag:** `pwn.college{YM7EhdB4WrPV0-7PIYU3-vQmPGV.QXzMDO0wyM0EzNzEzW}`

I give ~/c as the argument to the "_/challenge/run_" command which copies the flag to "c" in the home directory and then returns it to us. I used "**~**" symbol because it is the shorthand for the home directory (in our case i.e. /home/hacker) and since we could only use 3 characters in the argument.

```bash
hacker@paths~home-sweet-home:~$ /challenge/run ~/c
Writing the file to /home/hacker/c!
... and reading it back to you:
pwn.college{YM7EhdB4WrPV0-7PIYU3-vQmPGV.QXzMDO0wyM0EzNzEzW}
```

### New Learnings
1. Every user has a _home_ directory which can be represented by "**~**".
2. Arguments can have a character limit.

### References 
-NA-