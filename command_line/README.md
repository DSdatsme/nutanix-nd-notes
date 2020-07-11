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

<details>

<summary>4th July, 2020</summary>

## Terminal Tips

For all the terminal geeks who love to beautify their terminal here is a great resource.
> **warning**: not for purists.
https://drasite.com/blog/Pimp%20my%20terminal

## Terminal Tour

This week we will be covering search methods in the command line.

We already covered the use of wildcard in the pattern description. Today we will see a few more methods.

It is often necessary to use wildcard characters or other special characters as ASCII without attribution to their special function.
To do this we will use  `\`  to specify them. Example, if need to find the $ in the text we will specify it as `\$` , and similarly so.

To find the lines that begin with the pattern we will use `^`
ex: `^GNU` will match all the lines that begin with GNU.

The character `^`  has a different function within `[]`.
Here the `^` specifies which characters not to match with.
ex: if we had

```text
code
mode
bode
```

and used `[^c]ode` for matching we will only retrieve mode and bode and not code as we negated it.
Just like `^` we can use `$` to match and return lines in which pattern occurs at the end.
ex: `good$` will match all lines that end with good

## Terminal Test

A quick quiz on today's concepts (expecting answers in the thread):
Assume that the search string contains this:

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

What do these pattern match ?

1. `^[A-Za-z]*`
2. `copy*$`
3. `disclaimer.`
4. `permission\.`

</details>

<details>

<summary>6th July, 2020</summary>

## Terminal Tips

1. Listing processes by memory consumption (for cpu consumption change 4 to 3)
```bash
ps aux | sort -nk 4
```
2. You can run file downloads in the background `nohup wget <download URL>`
3. Often if we forget and run a cmd without root permission you just need to `sudo !!` to run the previous cmd under root.

## Terminal Tour

We will continue with one last post on pattern description in regular expressions.

We can define pattern repetition number as well with `{}` after the pattern.
ex: `[a-z]{3}` this expression matches all the small lettered three letter words in the document. Here, `[a-z]` matches small letters while `{3}` defines the number of times this pattern needs to repeat.

Another ability is to define an alternate pattern for match with `|`
ex: `good|bad` matches either the pattern good or bad.

We can perform grouping of patterns to create a more complex expression using `()`
ex: `(runn|us)ing` matches either running or using.

The above methods come under extended regular expressions and hence need an `-E` flag to run with grep.

## Terminal Test

given that the search string contains the following :

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

find the lines that these pattern match:

1. `(Re)?distribution*`
2. `*tion`
3. `(prior|endorse)`
4. `[fn]?or`

</details>

<details>

<summary>7th July, 2020</summary>

## Terminal Tips

1. using xargs to pass the output of one cmd to another as a formatted input(ex: copying all the .conf files listed in the /etc/ directory to Desktop)
`ls /etc/*.conf | xargs -i cp {} /home/user/Desktop`
2. To record you shell session i.e. all the commands that you have typed you can use the `script` begin the session with  `script`  and when done enter `exit` to stop the records. (all cmds will be saved in typescript)
3. Often when multiple terminal sessions are running the history of only one session is stored. To ensure that the history of all the concurrent sessions are stored we need to enable it as follows
`shopt -s histappend`

## Terminal Tour

We discussed the various intricacies of regular expression patterns and looked at their use in search.

### Description

Today we will give a brief look at sed (stream editor) sed unlike grep not only searches for patterns but also helps in editing them.

We will see a few functions that we can achieve with sed. We will mainly discuss the substitution operator

### Usage

`sed 's/<pattern>/<replacement text>/' file.txt`

If there is a need to replace text only within a range of lines we can modify the above as
`sed '<beg>,<end> s/<pattern>/<replacement text>/' file.txt`

Here `beg` is the line number we need to begin replacement similarly `end` defines the last line till which we perform the op.
If there is a need to specify the end of the line without it's the knowledge we can do so with substituting `end` with `$`.

We can perform deletion instead of substitution as follows

```sh
sed 'nd' file.txt
```

where n is the nth line that needs to be deleted.

A range can also be specified as we did above during substitution

```sh
sed '<beg>,<end>d' file.txt
```

or when a pattern needs to be deleted the following will work

```sh
sed '/<pattern>/d' file.txt
```

## Terminal Trouble

When the hard disk gets old there are a variety of problems that come to fore. The main is the falling speed of the process execution.
Often OS does a lot of bookkeeping tasks with caching files at many levels. One of them is caching in the hard disk. This is a great boon to fast execution but when the hard disk is about to fail every operation is heavy due to avoiding errors and it also damages the hard disk as
more read/write ops are performed. To avoid this in a system with a good amount of RAM we can reduce the swappiness as follows.

You can check your current swappiness with

```sh
cat /proc/sys/vm/swappiness
```

- Set the value for the running system.

```sh
sudo sh -c 'echo # > /proc/sys/vm/swappiness'
```

Here # is the number that needs to be set it can vary from 0 (none) - 60 (aggressive swapping)
A value of 10 is usually suggested.

- Backup `sysctl.conf`.

```sh
sudo cp -p /etc/sysctl.conf /etc/sysctl.conf.'date +%Y%m%d-%H:%M'
```

- Set the value in  `/etc/sysctl.conf` , so it stays after the reboot.

```sh
sudo sh -c 'echo "" >> /etc/sysctl.conf'
sudo sh -c 'echo # >> /etc/sysctl.conf'
sudo sh -c 'echo "vm.swappiness = #" >> /etc/sysctl.conf'
```

</details>

<details>

<summary>9th July, 2020</summary>

## Terminal Tips

1. Replacing a set of character with another in a file using tr (ex : small to caps )

```sh
cat file.txt | tr 'a-z' 'A-Z' > out.txt
```

2. Often typing all the args that we gave to previous command can be cumbersome.

To use the args from previous cmds we can do so with !* ( ex: setting file permission for newly created files)

```sh
touch file1 file2 file3
chmod +777 !*
```

3. It is often good to know the most used cmd and their frequency to set aliases ar simply for profiling

```sh
history | awk 'BEGIN {FS="[ \t]+|\\|"} {print $3}' | sort | uniq -c | sort -nr | head
```

## Terminal Tour

This week we will look at terminal tools for system management. Often we work on an SSH to a distant server. This has several issues, the prominent among which is the broken pipeline.
When large diagnostics or file transfers are run and the pipeline is broken, a lot of work is lost. Today we will discuss on a tool to mitigate this. **tmux** also known as a terminal multiplexer, allows you to have multiple terminal commands and applications running visually next to each other in an independently running terminal instance. This allows you to run various tasks without interruption from a broken pipeline or network error.

A tmux session is an independent entity from which we can be 'attached' or 'detached' from
Once tmux is installed with the following commands:

```sh
sudo apt update
sudo apt install tmux
```

You can create a session in tmux as follows:

```sh
tmux new -s <session-name>
```

The session-name can be for example 'file transfer' or anything meaningful that describes the process that needs to
run without interruption.

Once the session is created to work in this session you need to attach to it, which is done as follow:

```sh
tmux attach -t <session-name>
```

Now all the terminal commands that you run will be run independently in this session and can be monitored by attaching to this session. While a process is running we can detach from it and allow it to run in the background with the keys:

```sh
Ctrl + b ,  d.
```

Once you are done with your work in a particular session you can close it with:

```sh
tmux kill-session -t <session-name>
```

and to list all the available sessions

```sh
tmux ls
```

will do.

The cheat sheet provided below will help you with many other features that are present in tmux.
https://tmuxcheatsheet.com/

</details>
