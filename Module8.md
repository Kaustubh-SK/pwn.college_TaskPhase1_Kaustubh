# Data Manipulation

## Translating characters
In this challenge _/challenge/run_ prints the flag but the casing of all the letters is swapped, we need to fix that with _tr_.

### Solve
**Flag:** `pwn.college{c9E9k2Rl-uUKv4g-6Iddrwi4upz.01MxEzNxwyM0EzNzEzW}`

I piped the _stdout_ of _/challenge/run_ into the _stdin_ of _tr_. Then in order to swap the casing I first typed out all the alphabets in upper case then in lower case as the first argument of _tr_ and all the alphabets in lower case then in upper case as the second argument of _tr_. This swaps the casing of all the letters.

```bash
hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabc
defghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{c9E9k2Rl-uUKv4g-6Iddrwi4upz.01MxEzNxwyM0EzNzEzW}
```

### New Learnings
1. The _tr_ command translates the characters provided in its first argument to the characters provided in its second argument, in the given order.

### References 
-NA-


## Deleting characters
In this challenge _/challenge/run_ prints the flag but it conatins '^' and '%' as decoy characters in between the flag. We need to delete them using _tr_ and it's _-d_ flag.

### Solve
**Flag:** `pwn.college{Mte88S-YdAwovd7Sb0IGZA91oCy.0FNxEzNxwyM0EzNzEzW}`

I piped the _stdout_ of _/challenge/run_ into the _stdin_ of _tr_. Then in order to delete the decoy charcters I gave the flag '_-d_' to _tr_ and the '^%' as the argument, this deletes the decoy characters and gives the cleaned up flag.

```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{Mte88S-YdAwovd7Sb0IGZA91oCy.0FNxEzNxwyM0EzNzEzW}
```

### New Learnings
1. The _tr_ command can have a _-d_ flag that is used to delete the characters mentioned in the srgument of the command.

### References 
-NA-


## Deleting newlines
In this challenge _/challenge/run_ prints the flag but it conatins multiple newlines in between the flag. We need to delete them using _tr_, it's _-d_ flag and the escpaed newline character.

### Solve
**Flag:** `pwn.college{MMtsDT3cbsanW7WnY2Q9Av0FD9d.0VNxEzNxwyM0EzNzEzW}`

I piped the _stdout_ of _/challenge/run_ into the _stdin_ of _tr_. Then in order to delete the newlines I gave the flag '_-d_' to _tr_ and the "**'\n'**" as the argument(with the quotes), this deletes the newlines and gives the cleaned up flag in a single line.

```bash
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{MMtsDT3cbsanW7WnY2Q9Av0FD9d.0VNxEzNxwyM0EzNzEzW}
```

### New Learnings
1. The _tr_ command with the _-d_ flag can be used to delete newlines by giving "**'\n'**" as the argument.

### References 
-NA-


## Extracting the file lines with head
In this challenge _/challenge/pwm_ outputs a bunch of data but need to pipe the first 7 lines of this data to _/challenge/college_. If done correctlt this will provide us with the flag.

### Solve
**Flag:** `pwn.college{sZSvt9zjV1MFemzOUd7HvKIO7KH.0lNxEzNxwyM0EzNzEzW}`

I piped the _stdout_ of _/challenge/pwm_ into the _stdin_ of _head_. Then in order to get just the first 7 lines I gave the flag '_-n_' with '7' as argument then piped that into _/challenge/college_. This gave me the flag.

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{sZSvt9zjV1MFemzOUd7HvKIO7KH.0lNxEzNxwyM0EzNzEzW}
```

### New Learnings
1. The _head_ command is used to get the first few lines of a file.
2. By default it shows the first 10 lines of a file, but this can be changed by using the _-n_ flag and then specifyinh the number of lines required after that.

### References 
-NA-


## Extracting specific sections of text
In this challenge _/challenge/run_ outputs a bunch of lines and single characters (characters of the flag) as columns. We need to extract the flag characters and then join them together by removing the newlines.

### Solve
**Flag:** `pwn.college{Adq_JNyoKSGHeyQS1sWEUxI692g.01NxEzNxwyM0EzNzEzW}`

First I just invoked _/challenge/run_ to check the column number of the flag characters which was 2(I didn't mention it in the code below as it would make it unneccessarily long). Then I piped the output of _/challenge/run_ into _cut_ where I gave white space(" ") as the column delimiter using '_-d_' argument and then I used the '_-f_' argument with the value '2' to specify the column I wish to extract. Then this is piped to _tr_ with '_-d_' as the first argument and the "**'\n'**" as the second argument(with the quotes), this deletes the newlines and gives the cleaned up flag in a single line.

```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | 
tr -d '\n'
pwn.college{Adq_JNyoKSGHeyQS1sWEUxI692g.01NxEzNxwyM0EzNzEzW}
```

### New Learnings
1. The _cut_ command is used to extract specific columns of data from a text file.
2. It's '_-d_' and '_-f_' arguments are used to specify the column delimiters(how columns are separated) and the columns number to extract, respectively.

### References 
-NA-


## Sorting data
In this challenge teh file _/challenge/flags.txt_ contains 100 fake flags with the real flag mixed among them. However, when the flags are sorted alphabetically the real flag will be at the end. Thus we need to retrieve it.

### Solve
**Flag:** `pwn.college{UmIYyjI1g2d0JvMVopW2ke_29y0.0FM0MDOxwyM0EzNzEzW}`

I gave the file _/challenge/flags.txt_ as argument to the _sort_ command, this sorts the file alphabetically and prints it. Then as mentioned in the question I retrieved the last sorted flag.

```bash
hacker@data~sorting-data:~$ sort /challenge/flags.txt
ovm.colkege{UmIYyjI1f2c0JuLVopW2ke_29y0.0EM0MDNxvyL0EzMyEzW}
ovm.college{TlIYyjI1f1d0JvMVopW1je_29x0.0FM0LDNwwyM0EzNzEyW}
ovn.bnllefd{UmIYyjI1f2c0JvMUopV2je_18x0.0FM0MDOwwyL0EzMzEyW}
ovn.bokkege{TmIYyjH1g1c0JuMVnpV2ke_29y0.0FM0MDOwwxL0EyMyDyW}
ovn.bollefe{TmIYxjI0g1c0IvMVopV2ke_28y0.0FM0LDOwwyL0EzNzEyW}
....
....
pwn.college{UmIYyjI1f2d0JvMVopW1ke_29y0.0FM0MDNxwyM0EzNzEzW}
pwn.college{UmIYyjI1f2d0JvMVopW2kd_29y0.0FM0MDOwwyM0EzNzEzW}
pwn.college{UmIYyjI1g2d0JvMVnpW2ke_29y0.0FM0MDOxvyM0EzNzEzW}
pwn.college{UmIYyjI1g2d0JvMVopW2ke_29y0.0FM0MDOxwyM0EzMzEzW}
pwn.college{UmIYyjI1g2d0JvMVopW2ke_29y0.0FM0MDOxwyM0EzNzEzW}
```

### New Learnings
1. The _sort_ command is used to sort data from a files or output lines of commands.
2. By default it sorts them alphabetically, but we can give them '_-r_','_-n_','_-u_' and '_-R_' as arguments to sort them in reverse, sort numbers, sort only unique lines only(removes duplicates) and sorts in random order, respectively.

### References 
-NA-