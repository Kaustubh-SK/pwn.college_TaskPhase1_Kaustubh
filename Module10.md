# Untangling Users

## Becoming root with su
In this challenge we need to escalate to root with '_su_' by giving it '**hack-the-planet**' as password. Then we need to read the flag.

### Solve
**Flag:** `pwn.college{Elg8LUIxQW185Z_5rkMqfQmY3gs.QX1UDN1wyM0EzNzEzW}`

I ran _su_ and when it asked me for the password I copy pasted it and pressed enter(for some reason the password did'nt show up in the terminal when I pasted it), this made me the root user and thus now I could access all the files. So I _catted_ the _/flag_ file to get the flag.

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{Elg8LUIxQW185Z_5rkMqfQmY3gs.QX1UDN1wyM0EzNzEzW}
```

### New Learnings
1. The _su_ command is used to escalate as the 'root' user(if no argument is given), but it asks for a password to so so.
2. But _su_ is old and obsolete in modern systems which use other methods for authentication, rather than passwords.
3. The _sudo_ command is the modern counterpart of _su_.

### References 
-NA-


## Other users with su
In this challenge we need to switch to the '**zardus**' user with '_su_' by giving it '**dont-hack-me**' as password. Then we need to run _/challenge/run_ to get the flag.

### Solve
**Flag:** `pwn.college{kEA42SQtrTLTpyqhFmzRUzBZpV4.QX2UDN1wyM0EzNzEzW}`

I ran _su_ with '_zardus_' as argument and when it asked me for the password I copy pasted it and pressed enter(for some reason the password did'nt show up in the terminal when I pasted it), this switched me to the _zardus_ user, then I ran _/challenge/run_ and got the flag.

```bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /ch*/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kEA42SQtrTLTpyqhFmzRUzBZpV4.QX2UDN1wyM0EzNzEzW}
```

### New Learnings
1. The _su_ command is used to switch users by giving them as arguments to it.

### References 
-NA-


## Cracking passwords
There has been a password leak in _/challenge/shadow-leak_, in this cahllenge we need to crack it(using John the Ripper), then _su_ to _zardus_ by using that password and finally run _/challenge/run_ to get he flag.

### Solve
**Flag:** `pwn.college{oyecevnb-katE_i_eVM5hALkF4Y.QX3UDN1wyM0EzNzEzW}`

I ran _john_ with '_--show_' as argument to display the cracked passwords. Then I switched user to _zardus_ in the same way as before by copy pasting the password and pressing enter(for some reason the password did'nt show up in the terminal when I pasted it), this switched me to the _zardus_ user, then I ran _/challenge/run_ and got the flag.

```bash
hacker@users~cracking-passwords:~$ john --show /ch*/sh*
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20361:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /ch*/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oyecevnb-katE_i_eVM5hALkF4Y.QX3UDN1wyM0EzNzEzW}
```

### New Learnings
1. The _john_ command is used to crack user passwords.
2. We can give the '_--show_' argument to see the cracked passwords.

### References 
-NA-


## Using sudo
In this challenge we have been given _sudo_ access and we need to use it to get the flag.

### Solve
**Flag:** `pwn.college{glWeD7lJvIKdc3S_U8V-IOUeYn5.QX4UDN1wyM0EzNzEzW}`

Fitst I typed _sudo_ this gave me root access for that particular command, thus I use my privilege to _cat_ the _/flag_ file to get the flag.

```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{glWeD7lJvIKdc3S_U8V-IOUeYn5.QX4UDN1wyM0EzNzEzW}
```

### New Learnings
1. The _sudo_ command gives root access but only for that line of command, it dosn't launch a root shell like _su_.

### References 
-NA-