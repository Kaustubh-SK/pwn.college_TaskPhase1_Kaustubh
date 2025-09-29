# File Globbing

## Matching with *
In this challenge we need to change our directory to _/challenge_ but we can't give more than 4 characters as argument to _cd_, we must use '*'. Once in, we need to run _/challenge/run_ to get the flag.

### Solve
**Flag:** `pwn.college{gZbFQOBANPY93IjDirrVZWkOBF-.QXxIDO0wyM0EzNzEzW}`

I used '*' glob to shorten the path _/challenge_ to _/ch\*_, this limits the path to 4 characters(as required).

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /ch*/r*
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gZbFQOBANPY93IjDirrVZWkOBF-.QXxIDO0wyM0EzNzEzW}
```

### New Learnings
The '*' glob makes the shell find a directory or file that matches with the pattern before it, this shortens the paths.

### References 
-NA-


## Matching with ?
In this challenge we need to change our directory to _/challenge_ but we have to use '**?**' glob instead of _c_ and _l_. Then get the flag by running _/challenge/run_.

### Solve
**Flag:** `pwn.college{AapqD83QefJYxdny8_DHmE7t40w.QXyIDO0wyM0EzNzEzW}`

I used '?' glob inplce of _c_ and _l_ in the argument given to _cd_ and when I was inside I ran _/challenge/run_ to get the flag(even here I used '?' instead of c and l)

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /?ha??enge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{AapqD83QefJYxdny8_DHmE7t40w.QXyIDO0wyM0EzNzEzW}
```

### New Learnings
The '?' glob works like '*' but the shell only matches one single character.

### References 
-NA-


## Matching with []
In this challenge we need to change our directory to _/challenge/files_ and run _/challenge/run_ with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

### Solve
**Flag:** `pwn.college{U8RYI-PjaSxoCeiv14Ih0rP7JQF.QXzIDO0wyM0EzNzEzW}`

First I changed my directory and then when giving the argument to _/challenge/run_ I wrote "file_[bash]", this limits the search of the shell to only 4 characters 'b','a','s' and 'h' and thus gives us the flag.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{U8RYI-PjaSxoCeiv14Ih0rP7JQF.QXzIDO0wyM0EzNzEzW}
```

### New Learnings
The '[]' glob works like '?' but we limit the characters it searches for by specifying them in the square brackets.

### References 
-NA-


## Matching paths with []
We need to run _/challenge/run_(from the home directory) with a single argument that bracket-globs into the absolute paths of nultiple files in _/challenge/files_.

### Solve
**Flag:** `pwn.college{kRsQ_rEd8vOpj--Y51GiTGXHLl3.QX0IDO0wyM0EzNzEzW}`

In the argument  of _/challenge/run_ I used bracket-globing to include multiple files(file_[bash]) to be run. This gives the flag.

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{kRsQ_rEd8vOpj--Y51GiTGXHLl3.QX0IDO0wyM0EzNzEzW}
```

### New Learnings
The '[]' glob works on paths.

### References 
-NA-


## Multiple globs
We need to go to the _/challenge/files_ directory and then run _/challenge/run_ with an argument that covers evry word with the letter 'p' in them. The argument must be 3 or less characters.

### Solve
**Flag:** `pwn.college{Ao9Ybf3TRVQQyyFwtczO7vb4dn6.0lM3kjNxwyM0EzNzEzW}`

After moving in the requested directory, I gave the argument '\*p\*'. This ensures that all words with 'p' in them are covered as '*' before and after 'p' means _anything_(including _nothing_) can be before and after 'p'.

```bash
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{Ao9Ybf3TRVQQyyFwtczO7vb4dn6.0lM3kjNxwyM0EzNzEzW}
```

### New Learnings
We can have multiple globs in a single word.

### References 
-NA-


## Mixing globs
In this challenge we'll be using the previously learned globbing techniques together. We need to give an argument of 6 or less words to _/challenge/run_ in the _/challenge/files_ directory that will match all three of these files: "challenging", "educational", and "pwning".

### Solve
**Flag:** `pwn.college{02OloZDYZqATFJySc-fJQOyrQQ6.QX1IDO0wyM0EzNzEzW}`

First I changed the directory to _/challenge/files_. Since the first letter is different for all three files I use [] to bracket globe the that letter and then used '*' meaning that these letters can be followed by _anything_. This works because I know that there are no files other than these that start with c,e or p, this is because I saw all files using _ls_.

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      educational  incredible  magical     queenly    uplifting   youthful
beautiful    fantastic    jovial      nice        radiant    victorious  zesty
challenging  great        kind        optimistic  splendid   wonderful
delightful   happy        laughing    pwning      thrilling  xenial
hacker@globbing~mixing-globs:/challenge/files$ 
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{02OloZDYZqATFJySc-fJQOyrQQ6.QX1IDO0wyM0EzNzEzW}
```

### New Learnings
Different types of globbing can be merged into one word.

### References 
-NA-


## Exclusionary globing
We need to go to the _/challenge/files_ directory and then run _/challenge/run_ with an argument that runs all files that don't start with a p,w or n.

### Solve
**Flag:** `pwn.college{o_BEfD2rRHkT_q0C0gJs5JmVHr_.QX2IDO0wyM0EzNzEzW}`

After moving in the requested directory, I gave the argument '[^pwn]\*'. Using '^' means that files with p,w or n in that position will not be invoked and using '*' after it means that the rest of the name after that position(firrst position in our case) can be anything.

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{o_BEfD2rRHkT_q0C0gJs5JmVHr_.QX2IDO0wyM0EzNzEzW}
```

### New Learnings
We us '^'(only works in newer versions of bash) or '!'(works in all versions but can be confusing as it has a different meaning outside of being the first characetr in []) as the first character indie [] to invert the effect of bracket-globbing.

### References 
-NA-


## Tab completion
We need to _cat_ the _/challenge/pwncollege_ file but using <TAB\> to auto-complete the path.

### Solve
**Flag:** `pwn.college{k1vX9699DdgP4RbrPIU_O2clf-E.0FN0EzNxwyM0EzNzEzW}`

I typed _cat /c<TAB\>_ and it expanded to _cat /challenge/_, then I continued _cat /challenge/p<TAB\>_ and it expande to _cat /challenge/pwncollege_. Then I just pressed enter and got the flag.

```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{k1vX9699DdgP4RbrPIU_O2clf-E.0FN0EzNxwyM0EzNzEzW}
```

### New Learnings
<TAB\> can be used to auto-complete names of files and directories. This prevents accidental invoking of files that can happen in globbing.

### References 
-NA-


## Multiple options for tab completion
This challenge has multiple similarly named file in _/challenge/files_, we need to tab complete our way to the flag.

### Solve
**Flag:** `pwn.college{U1EA_fVPlvxI0AkqrC--IOk2yXe.0lN0EzNxwyM0EzNzEzW}`

1. I typed _cat /c<TAB\>_ and it expanded to _cat /challenge/_, then I continued _cat /challenge/f<TAB\>_ and it expande to _cat /challenge/files/_.
2. Then _cat /challenge/files/p<TAB\>_ expanded to _cat /challenge/files/pwn_. Pressing _TAB_ again gave a list of all files starting with 'pwn', so I typed _cat /challenge/files/pwnc<TAB\>_ which expanded to _cat /challenge/files/pwncollege-_.
3. Pressing _TAB_ again gave a list of files starting with 'pwncollege-'.
4. Then I completed it to _cat /challenge/files/pwncollege-flag_ becuase using more _TAB_ would useless as 'flag' and 'flamingo' have common first 3 letters.

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking
pwn-the-planet         pwncollege-flamingo    
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege- 
pwncollege-family      pwncollege-flamingo    pwncollege-hacking
pwncollege-flag        pwncollege-flyswatter  
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{U1EA_fVPlvxI0AkqrC--IOk2yXe.0lN0EzNxwyM0EzNzEzW}
```

### New Learnings
Pressing <TAB\> when there are multiple files with the same previous characters, it gives a list of all such files.

### References 
-NA-

## Tab completion on commands
This challenge has a command that starts with 'pwncollege'. We need to run it bu _TAB-completing_ it.

### Solve
**Flag:** `pwn.college{MLJ7Ly2Avte7PSEj4Sr_nSgb2q-.0VN0EzNxwyM0EzNzEzW}`

I typed _pwncollege<TAB\>_ and it expanded to _pwncollege-30919_ and executing this gave the flag.

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-30919 
Correct! Here is your flag:
pwn.college{MLJ7Ly2Avte7PSEj4Sr_nSgb2q-.0VN0EzNxwyM0EzNzEzW}
```

### New Learnings
Even commnads can be auto-completed using _TAB_ but it can also be risky if not double-checked.

### References 
-NA-
