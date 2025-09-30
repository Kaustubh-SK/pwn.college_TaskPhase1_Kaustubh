# Processes and Jobs

## Listing Processes
In this challenge _/challenge/run_ has been renamed to a random file name, but it has been launched so it should be findable in the running processes. We need to find the renamed file and relaunch it to get the flag.

### Solve
**Flag:** `pwn.college{wqzmA4hpV4z3kqWVxbus9KtjkZc.QX4MDO0wyM0EzNzEzW}`

I used _ps aux_ to list all the processes, there I looked for the renmaed file and found it as there was only one process that was running and had _/challenge_ as it's directory. So I relaunched it and got the flag.

```bash
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   16:31   0:00 /sbin/docker-init --
root           7  0.1  0.0 231708  2560 ?        S    16:31   0:00 /run/dojo/bin/sleep 
root         132  0.0  0.0   4132  2560 ?        S    16:31   0:00 /challenge/7379-run-
root         135  0.0  0.0   2744  1280 ?        S    16:31   0:00 sleep 6h
hacker       146  0.0  0.0  36972 22080 ?        Sl   16:31   0:00 /nix/store/g0q8n7xfj
hacker       150  0.0  0.0 231940  4160 pts/0    Ss   16:31   0:00 /run/dojo/bin/bash -
hacker       160  0.0  0.0 233600  3840 pts/0    R+   16:31   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/7379-run-7828
Yahaha, you found me! Here is your flag:
pwn.college{wqzmA4hpV4z3kqWVxbus9KtjkZc.QX4MDO0wyM0EzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### New Learnings
1. The _ps_ command is used to list the processes running in our terminal.
2. We give '_-ef_'(old) or '_aux_'(new) as an argument to _ps_ to greatly improve it's functionality. These arguments list all the processes in a more user readable format.

### References 
-NA-


## Killing Processes
In this challenge _/challenge/run_ will not run until _/challenge/dont\_run_ is running. We must find and _kill_ it and then run _.challenge/run_ to get the flag.

### Solve
**Flag:** `pwn.college{EFtzNl8_u-tzgVV658jrCH_WdZd.QXyQDO0wyM0EzNzEzW}`

I piped the output of _ps aux_ into _grep_ with '/ch*/don*' as argument, this gave me the information required (PID), then I used _kill_ to with the PID 136 to terminate _/challenge/dont\_run_. Then I ran _/challenge/run_ to get the flag.

```bash
hacker@processes~killing-processes:~$ ps aux | grep /ch*/don*
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker       136  0.0  0.0 231576  3520 ?        Ss   16:43   0:00 /challenge/dont_run
hacker       181  0.0  0.0 230696  2560 pts/1    S+   16:45   0:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /ch*/run
Great job! Here is your payment:
pwn.college{EFtzNl8_u-tzgVV658jrCH_WdZd.QXyQDO0wyM0EzNzEzW}
```

### New Learnings
1. The _kill_ command is used to kill a process running in our terminal.
2. It takes the PID of the running program as argument to terminate it.

### References 
-NA-


## Interrupting Processes
In this challenge _/challenge/run_ will not give us the flag until we interrupt it by pressing '**Ctrl+C**'.

### Solve
**Flag:** `pwn.college{sXr4UZA5FvU_mTuCbMYunWHQHqY.QXzQDO0wyM0EzNzEzW}`

I ran _/challenge/run_ and then pressed '**Ctrl+C**', this interrupts the process and gives me the flag.

```bash
hacker@processes~interrupting-processes:~$ /ch*/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{sXr4UZA5FvU_mTuCbMYunWHQHqY.QXzQDO0wyM0EzNzEzW}
```

### New Learnings
1. '**Ctrl+C**' hotkey is used to interrupt a running process that is expecting an input from the terminal, this causes the application to cleanly exit.

### References 
-NA-


## Killing Misbehaving Processes
In this challenge a decoy program has taken up a named FIFO file at _/tmp/flag\_fifo_ and _/challenge/run_ wants to write to it. So we need to kill this decoy and run _/challenge/run_ and then retrieve the flag.

### Solve
**Flag:** `pwn.college{0wdFQayyChTWoyRfogjlLYiUrws.0FNzMDOxwyM0EzNzEzW}`

First I checked all the running processes and found the decoy process as it was named '_/challenge/decoy_', with PID 142. So I killed it and then ran _/challenge/run_ which sent the flag to _/tmp/flag\_fifo_ (the named pipe). Finally I retrieved the flag by _catting_ the named pipe.

```bash
hacker@processes~killing-misbehaving-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   17:27   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.0  0.0 231708  2560 ?        S    17:27   0:00 /run/dojo/bin/sleep 6h
root         137  0.0  0.0   4132  1600 ?        S    17:27   0:00 /bin/bash /challenge/.init
root         138  0.0  0.0   4132  1600 ?        S    17:27   0:00 /bin/bash /challenge/.init
root         139  0.0  0.0   5204  3520 ?        S    17:27   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140  0.0  0.0   2744  1600 ?        S    17:27   0:00 sleep 6h
root         141  0.0  0.0   2744  1600 ?        S    17:27   0:00 sleep 6h
hacker       142  0.1  0.0  13516  9280 ?        Ss   17:27   0:00 /usr/bin/python /challenge/decoy
hacker       153  0.0  0.0  36972 21760 ?        Sl   17:27   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true /run/dojo
hacker       157  0.0  0.0 231972  4160 pts/0    Ss+  17:27   0:00 /run/dojo/bin/bash --login
hacker       167  1.1  0.0 231576  3520 pts/1    Ss   17:27   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       173  0.0  0.0 231972  4160 pts/1    S    17:27   0:00 /run/dojo/bin/bash --login
hacker       182  0.0  0.0 233600  3840 pts/1    R+   17:27   0:00 ps aux
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{0wdFQayyChTWoyRfogjlLYiUrws.0FNzMDOxwyM0EzNzEzW}
```

### New Learnings
1. Processes interfering with our work might need to be killed.

### References 
-NA-


## Suspending Processes
In this challenge _/challenge/run_ will not give us the flag until it sees another copy of itself already running and using the same terminal.

### Solve
**Flag:** `pwn.college{oIWnJ-TkiN53Ve6QedYeeFZRsh6.QX1QDO0wyM0EzNzEzW}`

I ran _/challenge/run_ and then pressed '**Ctrl+Z**', this suspends the process. Then I again run _/challenge/run_, this time it sees a copy of itself running in the same terminal and thus gives me the flag.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         161     151  0 17:37 pts/1    00:00:00 bash /challenge/run
root         163     161  0 17:37 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         161     151  0 17:37 pts/1    00:00:00 bash /challenge/run
root         168     151  0 17:37 pts/1    00:00:00 bash /challenge/run
root         170     168  0 17:37 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{oIWnJ-TkiN53Ve6QedYeeFZRsh6.QX1QDO0wyM0EzNzEzW}
```

### New Learnings
1. '**Ctrl+Z**' hotkey is used to suspend a running process that is expecting an input from the terminal, it is a much less drastic version of 'Ctrl+C'.

### References 
-NA-


## Resuming Processes
In this challenge _/challenge/run_ will not give us the flag until we first suspend it by pressing '**Ctrl+Z**' and then resume it using '_fg_' command.

### Solve
**Flag:** `pwn.college{wwG0CLAw--pgvsz2F9jlbBlUjce.QX2QDO0wyM0EzNzEzW}`

I ran _/challenge/run_ and then pressed '**Ctrl+Z**', this suspends the process then I invoke the _fg_ command with the _/challenge/run_ as argument, this resumes the most recently suspended process and gives us the flag.

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{wwG0CLAw--pgvsz2F9jlbBlUjce.QX2QDO0wyM0EzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

### New Learnings
1. The '_fg_' command is used to resume currently suspended processes.
2. Without any argument _fg_ resumes the most recently suspended process.

### References 
-NA-


## Backgrounding Processes
In this challenge _/challenge/run_ will not give us the flag until it sees a copy of itself running, not suspended.

### Solve
**Flag:** `pwn.college{UZoemQ6WDCE1cGf6MBwZ9EMQJTz.QX3QDO0wyM0EzNzEzW}`

I ran _/challenge/run_ and then pressed '**Ctrl+Z**', this suspends the process then I invoke the _bg_ command, this resumes the most recently suspended process in the background. Then I again run _/challenge/run_ and this time I get the flag as it sees a copy of itself running in the background.

```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         161 S+   bash /challenge/run
root         163 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         161 S    bash /challenge/run
root         171 S    sleep 6h
root         172 S+   bash /challenge/run
root         174 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{UZoemQ6WDCE1cGf6MBwZ9EMQJTz.QX3QDO0wyM0EzNzEzW}
```

### New Learnings
1. The '_bg_' command is used to resume currently suspended processes to the background.
2. Without any argument _bg_ resumes the most recently suspended process.

### References 
-NA-


## Foregrounding Processes
In this challenge _/challenge/run_ will not give us the flag until we suspend it, then background it and then foreground it, without suspending agin.

### Solve
**Flag:** `pwn.college{ECSN80YZpgy1SfuosUYqdkQe_5f.QX4QDO0wyM0EzNzEzW}`

I ran _/challenge/run_ and then pressed '**Ctrl+Z**', this suspends the process then I invoke the _bg_ command with the argument '_/ch*/run_' to put the process in the background. then I invoke the _fg_ command with the argument '_/ch*/run_' to put the process in the foreground, this gives me the flag.

```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /ch*/run
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg /ch*/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{ECSN80YZpgy1SfuosUYqdkQe_5f.QX4QDO0wyM0EzNzEzW}
```

### New Learnings
1. The '_fg_' command can also be used to directly move process from background to foreground.

### References 
-NA-


## Starting Backgrounding Processes
In this challenge _/challenge/run_ will not give us the flag until run it in the background by appending it with '**&**'.

### Solve
**Flag:** `pwn.college{4Vwh0HhD5Nj2Ei1U8PDpaFpQVSI.QX5QDO0wyM0EzNzEzW}`

I ran _/challenge/run_ but appended a '**&**' symbol to it. This ran the process in the background and thus gave us the flag.

```bash
hacker@processes~starting-backgrounded-processes:~$ /ch*/run &
[1] 161
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{4Vwh0HhD5Nj2Ei1U8PDpaFpQVSI.QX5QDO0wyM0EzNzEzW}

[1]+  Done                    /ch*/run
```

### New Learnings
1. We need to append '**&**' symbol to processes to run them in the background.

### References 
-NA-


## Process Exit Codes
In this challenge we must retrieve the exit code returned by _/challenge/get-code_ and give it as an argument to _/challenge/submit-code_ to get the flag.

### Solve
**Flag:** `pwn.college{oL32zzESL-c5hCZXuQolMLNjufi.QX5YDO1wyM0EzNzEzW}`

I ran _/challenge/get-code_ it exited with an exit code. In order to access it I use the '**?**' variable prepended with the '**$**' symbol(this is used to read its value), this gives me the error code as '34'. Then I give 34 as an argument to _/challenge/submit-code_ and this gives me the flag.

```bash
hacker@processes~process-exit-codes:~$ /ch*/get*
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
34
hacker@processes~process-exit-codes:~$ /ch*/sub* 34
CORRECT! Here is your flag:
pwn.college{oL32zzESL-c5hCZXuQolMLNjufi.QX5YDO1wyM0EzNzEzW}
```

### New Learnings
1. Every command in the shell exits with an exit code when it finishes and terminates.
2. Generally, commands that succeed return 0 and those that fail return 1 as thier exit code.
3. But they can be anyother specific code representing a particular failure mode.
4. We use the '**?**' variable prepended with '**$**' to access and read the exit code of the most-recently terminated command.

### References 
-NA-