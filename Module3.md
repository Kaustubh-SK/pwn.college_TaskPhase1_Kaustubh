# Comprehending Commands

## cat: not the pet, but the command!
In this challenge we need to read the flag from the _flag_ file in the home directory using '_cat_' command.

### Solve
**Flag:** `pwn.college{cZiDVVgTATtqTeUe42e1LQhoSDe.QXxcTN0wyM0EzNzEzW}`

I typed _cat flag_ and pressed enter to get the flag. 

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{cZiDVVgTATtqTeUe42e1LQhoSDe.QXxcTN0wyM0EzNzEzW}
```

### New Learnings
The '_cat_' command is used to diaply the content of one or more files, in the current working directory, on the terminal.

### References 
-NA-


## catting absolute paths
In this challenge we need to read the flag from the _flag_ file using it's absolute path.

### Solve
**Flag:** `pwn.college{A9dX2ksadKdAJ2iRmBfbCp6HTv_.QX5ETO0wyM0EzNzEzW}`

I typed _cat /flag_ and pressed enter to get the flag. Here '/flag' is the absolute path of the file.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{A9dX2ksadKdAJ2iRmBfbCp6HTv_.QX5ETO0wyM0EzNzEzW}
```

### New Learnings
The '_cat_' command is used to diaply the content of one or more files by using the absolute path of the files(s), on the terminal.

### References 
-NA-


## more catting practice
In this challenge we need to read the flag from the _flag_ file using it's absolute path. This time the file is in some random directory. We need to read the file without _cding_ into that directory.

### Solve
**Flag:** `pwn.college{8a68jjLATLeTOdBiXqA_XnQnut1.QXwITO0wyM0EzNzEzW}`

I typed the given absolute path of the _flag_ file after _cat_ to get the flag without cding into that directory.

```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by absolute path. Plus, I hid the flag in a different directory! You can find it in the file /usr/share/calendar/flag. Go cat it out **without** cding into that directory!

hacker@commands~more-catting-practice:~$ cat /usr/share/calendar/flag
pwn.college{8a68jjLATLeTOdBiXqA_XnQnut1.QXwITO0wyM0EzNzEzW}
```

### New Learnings
The absolute path given as an argument to _cat_ command can very as complex as it can.

### References 
-NA-


## comparing files
This challenge teaches us the '_diff_' command. We have to compare two files, one with 100 fake flags and the other with those same 100 fake flags and 1 correct flag, and get the correct flag.

### Solve
**Flag:** `pwn.college{Y1eynrNmOIXfvs1ITEOf5TtEW7e.01MwMDOxwyM0EzNzEzW}`

I type the path of the first file then the path of the second file as the argument of the _diff_ command, which gives me the result as the correct flag because that is the only thing different in both files. In this case the correct flag was added after the line 30 of file 1 in the line 31 of file 2.

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
30a31
> pwn.college{Y1eynrNmOIXfvs1ITEOf5TtEW7e.01MwMDOxwyM0EzNzEzW}
```

### New Learnings
The _diff_ command is used to compare two files line by line and shows exactly what's different between them. It takes the path of the first and second file as it's argument.

### References 
-NA-


## listing files
In this challenge, the '_run_' file has been renamed to some random name within the _challenge_ directory. We need to list all the files(usig the '_ls_' command) and directories in the _challenge_ directory and find the renamed _run_ file and execute it.

### Solve
**Flag:** `pwn.college{0i8Ya8ZuXlEfeMnd_vZJvFY7piA.QX4IDO0wyM0EzNzEzW}`

I listed the _challenge_ directory and found the renamed _run_ file and then executed this _renamed run_ file to get the flag.

```bash
hacker@commands~listing-files:~$ ls /challenge
14670-renamed-run-22141  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/14670-renamed-run-22141
Yahaha, you found me! Here is your flag:
pwn.college{0i8Ya8ZuXlEfeMnd_vZJvFY7piA.QX4IDO0wyM0EzNzEzW}
```

### New Learnings
The _ls_ command is used to list all the files and directories in the directory provided as the argument or in the current working directory if no argument is given.

### References 
-NA-


## touching files
In this challenge, we need to create two files(using _touch_ command), _pwn_ and _college_, in the _tmp_ directory. Then we can get the flag by running _/challenge/run_.

### Solve
**Flag:** `pwn.college{oXL89MoIczna-GBI-D56PbyfxSd.QXwMDO0wyM0EzNzEzW}`

First I created the _pwn_ file and then the _college_ file, both in the _tmp_ directory. I listed the _tmp_ directory to confirm the creation of both files and then got the flag.

```bash
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ ls /tmp
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{oXL89MoIczna-GBI-D56PbyfxSd.QXwMDO0wyM0EzNzEzW}
```

### New Learnings
The _touch_ command is used to create a blank file, either at the given path or in the current working directory.

### References 
-NA-


## removing files
In this challenge, we need to delete a file from the home directory using the '_rm_' command.

### Solve
**Flag:** `pwn.college{MQ_pQ7rQLdyoE3EeRUyIrNg8lO2.QX2kDM1wyM0EzNzEzW}`

Initially I listed the home directory to confirm the presence of the file that I want to delete, then I deleted using the '_rm_' command by giving the name of the file as the argument. Finally, I got the flag by running _/challenge/check_, which checks If I have deleted the requested file and gives me the flag if I have.

```bash
hacker@commands~removing-files:~$ ls
c  delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{MQ_pQ7rQLdyoE3EeRUyIrNg8lO2.QX2kDM1wyM0EzNzEzW}
```

### New Learnings
The _rm_ command is used to delete files or directories.

### References 
-NA-


## moving files
In this challenge, we need to move the _/flag_ file into _/tmp/hack-the-planet_ using the '_mv_' command.

### Solve
**Flag:** `pwn.college{c7sUK5aQQ2DOuTLASScrRlsHozT.0VOxEzNxwyM0EzNzEzW}`

I gave the path of the _flag_ file and then the path where I want to move it as arguments to the _mv_ command, this moves the file accordingly. Then I get the flag by running _/challenge/check_.

```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{c7sUK5aQQ2DOuTLASScrRlsHozT.0VOxEzNxwyM0EzNzEzW}
```

### New Learnings
The _mv_ command is used to move files around.

### References 
-NA-


## hidden files
In this challenge, we need to find the _flag_ which is in a hidden file inside the '**/**' directory.

### Solve
**Flag:** `pwn.college{wuJ8Gwao0P463B1dLzCaNL0D0vL.QXwUDO0wyM0EzNzEzW}`

I viewed the hidden file using the _ls -a_ command and then read the file using cat.

```bash
hacker@commands~hidden-files:~$ ls -a /
.           .flag-65622522914740  challenge  home   lib64   mnt  proc  sbin  tmp
..          bin                   dev        lib    libx32  nix  root  srv   usr
.dockerenv  boot                  etc        lib32  media   opt  run   sys   var
hacker@commands~hidden-files:~$ cat /.flag-65622522914740
pwn.college{wuJ8Gwao0P463B1dLzCaNL0D0vL.QXwUDO0wyM0EzNzEzW}
```

### New Learnings
Hidden files can be viewed by adding '**-a**' after _ls_.

### References 
-NA-


## An epic Filesystem Quest
Using _cd_,_ls_ and _cat_ commands we need to find the flag by following multiple clues spread throughout the file system. The first clue is in the _/_ directory.

### Solve
**Flag:** `pwn.college{EuVEb0rWnzqqhVM4USr45cxatJv.QX5IDO0wyM0EzNzEzW}`

I followed the clues until I got to the flag. When the clue mentioned 'hidden' clue I used '_ls -a_' to find it, when it said 'delayed' I first _cd-ed_ into the directory and then found the flag, when it said 'trapped' I accessed the clue without _cding_ into the directory.

```bash
hacker@commands~an-epic-filesystem-quest:~$ ls /
INFO  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:~$ cat /INFO
Great sleuthing!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/data/includes/cgc

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ls -a /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/data/includes/cgc
.   .TEASER    alpha.h  arm.h   ia64.h  powerpc.h    s390.h   sparc.h    thumb.h
..  aarch64.h  amd64.h  i386.h  mips.h  powerpc64.h  s390x.h  sparc64.h
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/pwndbg/.venv/lib/python3.8/site-pack
ages/pwnlib/data/includes/cgc/.TEASER
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ ls
WHISPER  arcx,anybus-controller.txt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ cat WHISPER
Tubular find!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/STIX/SizeTwoSym
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ ls /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/STIX/SizeTwoSym
Bold  DISPATCH  Regular
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ cat /usr/share/javascript/mathjax/unpacked/jax/
output/HTML-CSS/fonts/STIX/SizeTwoSym/DISPATCH
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/arch/x86/platform/geode

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ ls /opt/linux/linux-5.4/arch/x86/platform/geode
Makefile  TRACE-TRAPPED  alix.c  built-in.a  geos.c  net5501.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ cat /opt/linux/linux-5.4/arch/x86/platform/geod
e/TRACE-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/racket/pkgs/2d-doc/compiled
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ ls ^C
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ ls /usr/share/racket/pkgs/2d-doc/compiled
REVELATION  info_rkt.dep  info_rkt.zo
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ cat /usr/share/racket/pkgs/2d-doc/compiled/REVELATION
Tubular find!
The next clue is in: /opt/linux/linux-5.4/tools/power/cpupower/lib

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/fieldbus/Documentation/devicetree/bindings/fieldbus$ cd /opt/linux/linux-5.4/tools/power/cpupower/lib
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/lib$ ls
MEMO       cpufreq.h  cpuidle.h   cpupower.h
cpufreq.c  cpuidle.c  cpupower.c  cpupower_intern.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/lib$ cat MEMO
Lucky listing!
The next clue is in: /usr/share/doc/psmisc

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/lib$ ls -a /usr/share/doc/psmisc
.  ..  .CLUE  README.Debian  README.md  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/lib$ cat /usr/share/doc/psmisc/.CLUE
Congratulations, you found the clue!
The next clue is in: /usr/lib/x86_64-linux-gnu/perl/5.30.0/Tie

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/power/cpupower/lib$ cd /usr/lib/x86_64-linux-gnu/perl/5.30.0/Tie
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/perl/5.30.0/Tie$ ls
Hash  README
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/perl/5.30.0/Tie$ cat README
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{EuVEb0rWnzqqhVM4USr45cxatJv.QX5IDO0wyM0EzNzEzW}
```

### New Learnings
There can be files and directories that have conditioned placed onto them determining how and whe they can be viewed, like trapped once will self destruct if accessed inside their directory.

### References 
-NA-


## making directories
In this challenge, we need to make a new directory inside '_/tmp_' and then make a file inside that.

### Solve
**Flag:** `pwn.college{AkC7yv3e95YsiCQIO8jC37sDbzi.QXxMDO0wyM0EzNzEzW}`

First I moved in '_/tmp_' then crated a new directory '_/pwn_' and then cd-ed into it. There I created the file '_college_' and then got the flag by running _/challenge/run_.

```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{AkC7yv3e95YsiCQIO8jC37sDbzi.QXxMDO0wyM0EzNzEzW}
```

### New Learnings
The _mkdir_ command is used to create new directories.

### References 
-NA-


## linking files
In this challenge we need to get the flag by ticking the system using symbolic link. The flag is in '/flag' but it's not readable and '/challenge/catflag' instead reads '/home/hacker/not-the-flag'.

### Solve
**Flag:** `pwn.college{cxNng81qD5Zok6rR9L3y34K8FZf.QX5ETN1wyM0EzNzEzW}`

I used symbolic links to link '/home/hacker/not-the-flag' to the '/flag' file, this way when i execute '/challenge/catflag' it reads '/flag' instead of '/home/hacker/not-the-flag'.

```bash
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{cxNng81qD5Zok6rR9L3y34K8FZf.QX5ETN1wyM0EzNzEzW}
```

### New Learnings
The _ln_ command is used to create links between files. Adding a '_-s_' flag after it will create a symbolic link.
There are two types of links, hard and soft. Hard links are like addresses and soft links basically point to a file.

### References 
-NA-