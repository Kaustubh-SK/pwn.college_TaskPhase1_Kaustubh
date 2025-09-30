# Terminal Multiplexing

## Launching Screen
In this challenge we need to launch a new screen and that'll give us the flag.

### Solve
**Flag:** `pwn.college{M5pJ5gNQLgZLi6LogaDQSghpOJc.0VN4IDOxwyM0EzNzEzW}`

I typed _screen_ then pressed enter, then a different screen popped up. When I pressed '**Esc**' I came back to the terminal and got the flag.

```bash
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{M5pJ5gNQLgZLi6LogaDQSghpOJc.0VN4IDOxwyM0EzNzEzW}
```

### New Learnings
1. The _screen_ command is used to launch new virtual terminals inside our terminal.

### References 
-NA-


## Detaching and Attaching
In this challenge we need to launch a new screen detach it using '**Ctrl+A**' followed by 'd', then run _/challenge/run_(this send the flag to the dettached screen runningin the background), then rettach the screen using _screen -r_. Now here we can get our flag

### Solve
**Flag:** `pwn.college{EkJffW-PmAKAam3jqx6ZqR5Fch2.0lN4IDOxwyM0EzNzEzW}`

I typed _screen_ then pressed enter, then a in order to detach it I pressed '**Ctrl+A**' folloed by 'd', then I ran _/challenge/run_ which sent the flag to the dettached screen. Then I reattached that screen by using _screen -r_, here I got the flag.

```bash
#MAIN TERMINAL: 
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 162.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /ch*/run
Found detached screen session: 162.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You will find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r

#VIRTUAL SCREEN:
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{EkJffW-PmAKAam3jqx6ZqR5Fch2.0lN4IDOxwyM0EzNzEzW}
Yes! Flag is: pwn.college{EkJffW-PmAKAam3jqx6ZqR5Fch2.0lN4IDOxwyM0EzNzEzW}
```

### New Learnings
1. We can dettach a screen using '**Ctrl+A**' folloed by 'd'.
2. We can also reattach an already dettached file using _screen -r_.

### References 
-NA-


## Finding Sessions
This challenge has three screen sessions out of which one contains the flag and the rest are decoys. Check each one until you find the flag.

### Solve
**Flag:** `pwn.college{sqwZf_Q0Ok3jXvgKEr8j8yrKv5t.01N4IDOxwyM0EzNzEzW}`

I typed _screen -ls_ then pressed enter, this gave me tha name and PID of all the running screens. Then I used _screen -r PID_ for all the three screens and found the flag in the third screen.

```bash
#MAIN TERMINAL: 
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        332.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        384.pts-2.terminal-multiplexing~launching-screen        (Remote or dead)
        173.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        162.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_b1a76cdd6a000dbd    (Detached)
        147.session_1eb7defaebb480f1    (Detached)
        150.session_b69f78a9c94f6fd0    (Detached)
7 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_b1a76cdd6a000dbd]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
[detached from 147.session_1eb7defaebb480f1]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 150
[detached from 150.session_b69f78a9c94f6fd0]

#VIRTUAL SCREEN 1:
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Wrong session! Keep looking.'
Wrong session! Keep looking.

#VIRTUAL SCREEN 2:
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Nothing here! Try another session.'
Nothing here! Try another session.

#VIRTUAL SCREEN 3:
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{sqwZf_Q0Ok3jXvgKEr8j8yrKv5t.01N4IDOxwyM0EzNzEzW}
pwn.college{sqwZf_Q0Ok3jXvgKEr8j8yrKv5t.01N4IDOxwyM0EzNzEzW}
```

### New Learnings
1. We can speficy which screen we want to reattach by giving it's name or PID as an argument after _screen -r_.

### References 
-NA-


## Switching Windows
In this challenge we need to reattach a screen that has 2 windows (0 and 1). We need to go through the windows and find the flag.

### Solve
**Flag:** `pwn.college{kvKjT3xrgQ6I0qyvG0wTjf21ykj.0FO4IDOxwyM0EzNzEzW}`

I typed _screen -r_ then pressed enter, this reattached the screen which by default has window 0 opened(which didn't have the flag). I switched to the next window using '**Ctrl+A**' followed by 'n'. This window had the flag.

```bash
#MAIN TERMINAL: 
hacker@terminal-multiplexing~switching-windows:~$ screen -r

#VIRTUAL SCREEN 1:
 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!

#VIRTUAL SCREEN 2:
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{kvKjT3xrgQ6I0qyvG0wTjf21ykj.0FO4IDOxwyM0EzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{kvKjT3xrgQ6I0qyvG0wTjf21ykj.0FO4IDOxwyM0EzNzEzW}
```

### New Learnings
1. A single screen can have multiple windows.
2. The windows of a screen are handled with different keyboard shortcuts all starting with '**Ctrl+A**':
    - Ctrl-A c - Create a new window
    - Ctrl-A n - Next window
    - Ctrl-A p - Previous window
    - Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
    - Ctrl-A " - bring up a selection menu of all of the windows

### References 
-NA-


## Detaching and Attaching (tmux)
In this challenge we need to launch _tmux_, detach from it, then run _/challenge/run_(which sends the flag to the tmux screen) and then reattach the tmux screen and get the flag.

### Solve
**Flag:** `pwn.college{QTYlG4Ey0JFW6WsBrGg3VdinsxF.0VO4IDOxwyM0EzNzEzW}`

I typed _tmux_ then pressed enter, then a in order to detach it I pressed '**Ctrl+B**' followed by 'd', then I ran _/challenge/run_ which sent the flag to the dettached tmux screen. Then I reattached that screen by using _tmux a_, here I got the flag.

```bash
#MAIN TERMINAL: 
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /ch*/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You will find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a

#TMUX SCREEN:
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{QTYlG4Ey0JFW6WsBrGg3VdinsxF.0VO4IDOxwyM0EzNzEzW}
Congratulations, here is your flag: pwn.college{QTYlG4Ey0JFW6WsBrGg3VdinsxF.0VO4IDOxwyM0EzNzEzW}
```

### New Learnings
1. The _tmux_(terminal multiplexer) command is the newer version of screen.

### References 
-NA-


## Switching Windows (tmux)
This challenge has a tmux session with 2 windows, one with the flag. We need to get to the flag.

### Solve
**Flag:** `pwn.college{g2vWlVyLGZW6Cjdy8dyTs_uNLeU.0FM5IDOxwyM0EzNzEzW}`

I typed _tmux a_ then pressed enter, this reattached the tmux screen which had window 1 opened(which didn't have the flag). I switched to window 0 using '**Ctrl+B**' followed by '0'. This window had the flag.

```bash
#MAIN TERMINAL: 
hacker@terminal-multiplexing~switching-windows:~$ tmux a

#TMUX SCREEN 0:
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{g2vWlVyLGZW6Cjdy8dyTs_uNLeU.0FM5IDOxwyM0EzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{g2vWlVyLGZW6Cjdy8dyTs_uNLeU.0FM5IDOxwyM0EzNzEzW}

#TMUX SCREEN 1:
 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
```

### New Learnings
1. The windows of a tmux screen are handled with different keyboard shortcuts all starting with '**Ctrl+B**':
    - Ctrl-B c - Create a new window
    - Ctrl-B n - Next window
    - Ctrl-B p - Previous window
    - Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
    - Ctrl-B w - See a nice window picker

### References 
-NA-