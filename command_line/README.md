# Terminator
a daily bite of terminal for geeks

## 2nd July. 2020

### Terminal Tips

To clear the contents of the file without deleting it try:

```sh
truncate -s 0 file.txt
```

To list the number of directories or files in a folder:

```sh
tree folder/ | tail -1
```

To force kill processes from a certain program:

```sh
kill -9 $(pgrep <program-name>)
```

### Terminal Tou

This week we will be covering search methods in the command line.

**Description :**
We will begin with grep, a powerful pattern-matching tool.
Given one or more patterns, *`grep`* searches input files for matches to the patterns, the matching lines are copied to std output.
Manual:

```sh
grep [option...] [patterns] [file...]
```

option: here it includes a huge number of options that can be specified for pattern matching like ignoring case or attaching the pattern file.
pattern: A pattern can be a simple string or a  `regular expression` , we will cover regular expression in the coming days.
file: The file in which we will search for pattern.

Example:

```sh
grep myname file.txt
```

here the file.txt contains :

```sh
myname is xyz.
I am studying at so and so.
```

The output:

```sh
myname is xyz.
```

### Terminal Test

A quick quiz on how well you know the world of OSS.

1. Expand GNU.
2. Who wrote the linux kernel.
3. Who is the founder of Free Software Foundation.
4. What is Git.
