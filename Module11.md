# Perceiving Permissions

## Changing File Ownership
In this challenge we need to change the ownership of '_/flag_' from _root_ to _hacker_ using '_chown_'(for this challenge we can use _chown_ freely). Then access it to get the flag.

### Solve
**Flag:** `pwn.college{UMQin-y4kFJCtQvdxTh6C2E8qEn.QXxEjN0wyM0EzNzEzW}`

First I tried to _cat_ _/flag_ withour changing ownership, this didn't result in the flag. So I ran _chpwn_ with the username _hacker_ as the first argument and the filename _/flag_ as the second argument, this gave us the access to the flag. Now when I _catted_ the file I got the flag.

```bash
hacker@permissions~changing-file-ownership:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{UMQin-y4kFJCtQvdxTh6C2E8qEn.QXxEjN0wyM0EzNzEzW}
```

### New Learnings
1. The _chown_ command is used to change ownership of files from one user to another.
2. Generally _chown_ can only be used by _root_ user.

### References 
-NA-


## Groups and Files
In this challenge we need to change the group of '_/flag_' using '_chgrp_'(for this challenge we can use _chgrp_ freely). Then get the flag.

### Solve
**Flag:** `pwn.college{UXgW61nNkkhwGglqsmEfGvT9GDw.QXxcjM1wyM0EzNzEzW}`

I ran _chgrp_ with the groupname _hacker_ as the first argument and the filename _/flag_ as the second argument, this changed the group of _/flag_ to _hacker_. Now when I _catted_ the file I got the flag.

```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{UXgW61nNkkhwGglqsmEfGvT9GDw.QXxcjM1wyM0EzNzEzW}
```

### New Learnings
1. The _chgrp_ command is used to change the group of files from one to another.
2. Generally _chgrp_ can only be used by _root_ user.

### References 
-NA-


## Fun With Groups Names
In this challenge we need to change the group of '_/flag_' using '_chgrp_'(for this challenge we can use _chgrp_ freely), but this time our group has a random name. First we need to find that out by using _id_. Then get to the flag.

### Solve
**Flag:** `pwn.college{QKsh71LjflT0_St-KTOE5YF7jSv.QXycjM1wyM0EzNzEzW}`

First I used the _id_ command to find out the group in which my user(hacker) is in.Then I ran _chgrp_ with the groupname that I found out as the first argument and the filename _/flag_ as the second argument, this changed the group of _/flag_ to _grp19742_. Now when I _catted_ the file I got the flag.

```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp19742) groups=1000(grp19742)
hacker@permissions~fun-with-groups-names:~$ chgrp grp19742 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{QKsh71LjflT0_St-KTOE5YF7jSv.QXycjM1wyM0EzNzEzW}
```

### New Learnings
1. The _id_ command gives us our user-id, group-id and all the groups that we are in.

### References 
-NA-


## Changing Permissions
In this challenge we need to change the permission of '_/flag_' using '_chmod_' to read it. Then get the flag.

### Solve
**Flag:** `pwn.college{gOdXOLgvyiRaIiEAUwfCF9uNnWO.QXzcjM1wyM0EzNzEzW}`

First I used the _ls -l_ command on _/flag_ to find out its permissions. Then I ran _chmod_ and adding the '**o+r**' mode that now gives permissions to all the other users to read the file. Now then I _catted_ the file and got the flag.

```bash
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-------- 1 root root 60 Sep 30 13:14 /flag
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{gOdXOLgvyiRaIiEAUwfCF9uNnWO.QXzcjM1wyM0EzNzEzW}
```

### New Learnings
1. The _chmod_ command is used to change(modify or create new) permissions of a file.
2. Generally, inorder to chnage permisiions of a file we need to have the write permission of that file.

### References 
-NA-


## Executable Files
In this challenge we need to change the execution permission of '_/challenge/run_' using '_chmod_' to allow us to execute it. Then get the flag.

### Solve
**Flag:** `pwn.college{oL-UM6Ws-gSni8d75QKhgmwVGl7.QXyEjN0wyM0EzNzEzW}`

First I used the _ls -l_ command on _/challenge/run_ to find out its permissions. Then I ran _chmod_ and adding the '**a+x**' mode that now gives permissions to everyonr to execute the program. Then I executed it and got the flag.

```bash
hacker@permissions~executable-files:~$ ls -l /ch*/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /ch*/run
hacker@permissions~executable-files:~$ /ch*/run
Successful execution! Here is your flag:
pwn.college{oL-UM6Ws-gSni8d75QKhgmwVGl7.QXyEjN0wyM0EzNzEzW}
```

### New Learnings
1. Linux only executes a file if we have the execute access of that program file.

### References 
-NA-


## Permission Tweaking Practice
In this challenge we need to change the permissions of '_/challenge/pwn_' 8 times in a row and we need to get all of them correct or else it'll restart. We need to run _/challenge/run_ to start the gchallenge. When we complete all the 8 rounds, we can change the permissions of _/flag_ amd read it.

### Solve
**Flag:** `pwn.college{g9EINMaM6Ysn3WE8Wxjn-xuH3O2.QXwEjN0wyM0EzNzEzW}`

First I ran _/challenge/run_ to start the challenge. Then I simply followed each round's instructions and changed the required permissions. After 8 rounds I changed the reading permissions of _/flag_ so that everyone could read it. Then I _catted_ it and got the flag.

```bash
hacker@permissions~permission-tweaking-practice:~$ /ch*/run
Round 1 of 8!
Current permissions of "/challenge/pwn": rw-r--r--
Needed permissions of "/challenge/pwn": rw----r--

hacker@permissions~permission-tweaking-practice:~$ chmod g-r /ch*/pwn
You set the correct permissions!
Round 2 of 8!
Current permissions of "/challenge/pwn": rw----r--
Needed permissions of "/challenge/pwn": rwx---r--

hacker@permissions~permission-tweaking-practice:~$ chmod u+x /ch*/pwn
You set the correct permissions!
Round 3 of 8!
Current permissions of "/challenge/pwn": rwx---r--
Needed permissions of "/challenge/pwn": -w-------

hacker@permissions~permission-tweaking-practice:~$ chmod uo-rx /ch*/pwn
You set the correct permissions!
Round 4 of 8!
Current permissions of "/challenge/pwn": -w-------
Needed permissions of "/challenge/pwn": -w------x

hacker@permissions~permission-tweaking-practice:~$ chmod o+x /ch*/pwn
You set the correct permissions!
Round 5 of 8!
Current permissions of "/challenge/pwn": -w------x
Needed permissions of "/challenge/pwn": --------x

hacker@permissions~permission-tweaking-practice:~$ chmod u-w /ch*/pwn
You set the correct permissions!
Round 6 of 8!
Current permissions of "/challenge/pwn": --------x
* the world does have execute permissions
Needed permissions of "/challenge/pwn": ------r-x

hacker@permissions~permission-tweaking-practice:~$ chmod o+r /ch*/pwn
You set the correct permissions!
Round 7 of 8!
Current permissions of "/challenge/pwn": ------r-x
Needed permissions of "/challenge/pwn": rwx---r-x

hacker@permissions~permission-tweaking-practice:~$ chmod u+rwx /ch*/pwn
You set the correct permissions!
Round 8 of 8!
Current permissions of "/challenge/pwn": rwx---r-x
Needed permissions of "/challenge/pwn": rwx--xr-x

hacker@permissions~permission-tweaking-practice:~$ chmod g+x /ch*/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!
Current permissions of "/flag": ---------

hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{g9EINMaM6Ysn3WE8Wxjn-xuH3O2.QXwEjN0wyM0EzNzEzW}
```

### New Learnings
-NA-

### References 
-NA-


## Permissions Setting Practice
In this challenge we need to change the execution permission of '_/challenge/run_' using '_chmod_' to allow us to execute it. Then get the flag.

### Solve
**Flag:** `pwn.college{s9pPhf2P8DaoFDZ0-EEui0dUO7t.QXzETO0wyM0EzNzEzW}`

First I ran _/challenge/run_ to start the challenge. Then I simply followed each round's instructions and wrote new permissions to each of user,group and others. After 8 rounds I changed the wrote new permissions of _/flag_ so that everyone could read it. Then I _catted_ it and got the flag.

```bash
hacker@permissions~permissions-setting-practice:~$ /ch*/run
Round 1 of 8!
Current permissions of "/challenge/pwn": rw-r--r--
Needed permissions of "/challenge/pwn": --x--x-wx

hacker@permissions~permissions-setting-practice:~$ chmod a=x,o=wx /ch*/pwn
You set the correct permissions!
Round 2 of 8!
Current permissions of "/challenge/pwn": --x--x-wx
Needed permissions of "/challenge/pwn": r-x-w--wx

hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=w,o=wx /ch*/pwn
You set the correct permissions!
Round 3 of 8!
Current permissions of "/challenge/pwn": r-x-w--wx
Needed permissions of "/challenge/pwn": r---w-r--

hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=w,o=r /ch*/pwn
You set the correct permissions!
Round 4 of 8!
Current permissions of "/challenge/pwn": r---w-r--
Needed permissions of "/challenge/pwn": ---rwxr-x

hacker@permissions~permissions-setting-practice:~$ chmod u=-,g=rwx,o=rx /ch*/pwn
You set the correct permissions!
Round 5 of 8!
Current permissions of "/challenge/pwn": ---rwxr-x
Needed permissions of "/challenge/pwn": --xrwxrwx

hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=rwx,o=rwx /ch*/pwn
You set the correct permissions!
Round 6 of 8!
Current permissions of "/challenge/pwn": --xrwxrwx
Needed permissions of "/challenge/pwn": r--rwx--x

hacker@permissions~permissions-setting-practice:~$ chmod u=r,o=x /ch*/pwn
You set the correct permissions!
Round 7 of 8!
Current permissions of "/challenge/pwn": r--rwx--x
Needed permissions of "/challenge/pwn": r-----r--

hacker@permissions~permissions-setting-practice:~$ chmod g=-,o=r /ch*/pwn
You set the correct permissions!
Round 8 of 8!
Current permissions of "/challenge/pwn": r-----r--
Needed permissions of "/challenge/pwn": r--r-----

hacker@permissions~permissions-setting-practice:~$ chmod g=r,o=- /ch*/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!
Current permissions of "/flag": ---------

hacker@permissions~permissions-setting-practice:~$ chmod a=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{s9pPhf2P8DaoFDZ0-EEui0dUO7t.QXzETO0wyM0EzNzEzW}
```

### New Learnings
1. We use '**=**' with _chmod_ to assign new permissions, overwriting the old ones.
2. Also we can chain together multiple _chmod modes_ using '**,**'.

### References 
-NA-


## The SUID Bit
In this challenge we need to add the SUID bit to _/challenge/getroot_ in order to spawn a _root_ shell through which we can _cat_ the flag.

### Solve
**Flag:** `pwn.college{Elt9nWDlLAnJllSNVWExQ0Z-7d5.QXzEjN0wyM0EzNzEzW}`

First I add the SUID bit to _/challenge/getroot_ by givinng '**u+s**' as the first argument to _chmod_, then I run it. This takes me to a root shell where I _cat_ _/flag_ and get the flag.

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /ch*/getroot
hacker@permissions~the-suid-bit:~$ /ch*/get*
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{Elt9nWDlLAnJllSNVWExQ0Z-7d5.QXzEjN0wyM0EzNzEzW}
```

### New Learnings
1. The "Set User ID" (SUID) permissions bit allows a user to run a program as the owner of that program's file.
2. We can set a file's SUID bit by using '**chmod u+s [program]**'

### References 
-NA-