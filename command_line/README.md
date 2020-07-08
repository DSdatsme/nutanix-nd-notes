# Terminator
a daily bite of terminal for geeks

<details>

<summary>2nd July, 2020</summary>

## Terminal Tips

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

## Terminal Tour

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

## Terminal Test

A quick quiz on how well you know the world of OSS.

1. Expand GNU.
2. Who wrote the linux kernel.
3. Who is the founder of Free Software Foundation.
4. What is Git.

</details>

<details>

<summary>3rd July, 2020</summary>

## Terminal Tips

You end up in a long directory path and then you realize that you have to go back to the previous directory

```sh
cd -
```

Imagine a situation where you used a long command and you have to use it again

```sh
ctrl+r search term
```

To read the output well without overcrowding and as table, example when you read a mount file

```sh
mount | column –t
```

## Terminal Tour

This week we will be covering search methods in the command line.
Today, we will take a look at pattern matching with regular expressions in brief.
we saw that we can use grep as : `grep pattern file.txt`

Today we cover a specific pattern description called wildcards, So let's start.

- We use `.` to match any character before or after a set of ascii characters
ex: `..cept` can match the strings accept, except, etc.
- Similarly if we need to match more than one character we use `*`
ex: `cert*` can match the strings certificate, certification, etc.
- If we need to find strings with only certain characters before or after a set of ascii characters we cover them in `[]`
ex: `t[wo]o` matches both the strings too and two, as either w or o can be selected in the second character's place.
- If we need to specify rather a range of characters we can do so with specifying the first and last witht the hyphen `-` in the brackets
ex: `[A-Z]*` matches all the strings with capital letters like Arizona, The, etc.

## Terminal Test

A quick quiz on having grasped the above regular expressions.
Assume the search string contains this :

```text
1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of the University nor the names of its contributors
   may be used to endorse or promote products derived from this software
   without specific prior written permission.
```

What do these pattern match (write only the unique string):

1. `[N-R]*`
2. `co[pd]*`
3. `no..*`

</details>
