# Introduction to Unix
> **Things covered here**  
> *  Why familiarity with the command line is important
> *  Running commands and general syntax
> *  File-system structure and how to navigate
> *  Viewing, creating, and manipulating "plain-text" documents
> *  Pipes and redirectors
> *  Intro to wildcards

<br>

---
<br>

# Some terminology

- "**Unix**" – Unix is a type of operating system, or more precisely, a family of operating systems as the [wiki](https://en.wikipedia.org/wiki/Unix) words it. This is why you will hear people say things like “Unix-like”, and refer to Unix being on both Mac and Linux computers (they run Unix-like operating systems).

- “**command line**” or “**terminal**” – a text-based environment capable of taking input and providing output.

- “**shell**” – what runs in a terminal. The shell is your ambassador to your operating system so you can tell it very specific things; the shell translates our language into the computer’s language and then back again so we can understand the output.

- “**bash**” – a specific type of shell (by far the most common these days). This describes the programming language your shell understands.

<br>

---
<br>

# Why learn the command line?

*  enables use of non-GUI (Graphical User Interface) tools
*  reproducibility
*  automation of repetitive tasks
	*  need to rename 1,000 files?
	*  need to assemble 300 genomes?
*  enables use of higher-powered computers elsewhere (server/cloud)  
<br>

---
<br>

# Practice data!
For right now, and only for right now, I would like you to blindly copy and paste the following commands into your terminal window. This is so that we're all working in the same place with the same files. **I promise this will be the only time I ask you to do this.** At the end of this page, we'll revisit this and break it down :) 


```
cd ~
curl -O https://AstrobioMike.github.io/tutorial_files/unix_intro.tar.gz
tar -xvf unix_intro.tar.gz
rm unix_intro.tar.gz
cd unix_intro
```

<br>

---
<br>

# Running commands

## General structure of commands

The general syntax of a command is as follows: `command argument`. **Spaces are special!** The command line uses spaces to know how to properly break apart things. 

Arguments (often also referred to as "flags" or "options") can be **optional** or **required** based on the command. 

`date` is a command that prints out the date and time. It does not require any arguments:

```bash
date
```
But you can provide optional arguments to `date`. Here we are adding the `-u` argument to tell it instead of local time (the "default"): 

```bash
date -u
```

If we tried to enter this without the "space" separating `date` and the argument `-u`, the computer won't know how to break apart the command:

```bash
date-u
```

Some commands require arguments and won't work without them. `head` is a command that prints the first lines of a file, so it **requires** us to provide the file we want it to act on: 

```bash
head text.txt
```

Here "text.txt" is the **required** argument, and in this case it is also what's known as a **positional** argument. This is because we aren't identifying what it is with a preceding flag or anything. We are just listing it after the command, and the `head` command knows what to do with it. But this depends on how the command was written. Sometimes you need to specify the input file to a command (e.g. some commands will use the `-i` flag, but it's often other things as well).

If we ran `head` with no file to act on, it would get stuck. We know the terminal is still doing something (or trying to in this case) because our "prompt" hasn't returned. You can cancel an operation by pressing the "control" key and the "c" key simultaneously (`ctrl + c`). 

There are also optional arguments for the `head` command. The default for `head` is to print the first 10 lines of a file. We can change that by specifying the `-n` flag, followed by how many lines we want:

```bash
head -n 5 text.txt
```

Note that when we provided the `-u` flag to the `date` command (to get the command to print UTC time instead of local), we didn't need to provide any arguments to that particular flag (it's just on/off). But with the `-n` flag to `head`, we are specifying the number of lines we want to print out, so we have to provide a number in this case.

> This is the framework for how all things work at the command line! Multiple commands can be strung together, and some commands can have many options, inputs, and outputs and can grow to be quite long, but this general framework is underlying it all. **Becoming familiar with the baseline rules is important, memorizing particular commands and options is not!**

<br>

---
<br>

# File-system structure and moving around

## Absolute vs relative path


<h4><i>Commands presented in this section:</i></h4>

|Command     |Function          |
|:----------:|------------------|
|`pwd`       |tells you where you are in the computer (print working directory)|
|`ls`        |lists contents of a directory (list)|
|`cd`| changes directories |

<h4><i>Special characters presented in this section:</i></h4>

|Characters     | Meaning          |
|:----------:|------------------|
|`.`       | the current working directory |
|`../`        |specifies a directory one level "above" the current working directory|
|`~`| your "home" location |
| `/` | your computer's "root" location |
