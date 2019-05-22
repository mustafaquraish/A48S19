---
title: Using the Command Line
sidebar: 15
sidebar-title: Command Line
---

{% include toc header="" %}

---
## What is the command line, and why should I use it?
---
The command line (also called terminal) is an interface where you can directly execute commands on your computer. It allows you to traverse through all your directories, change settings, run files, [watch movies](https://www.instructables.com/id/How-to-Watch-Star-Wars-in-Terminal/) and the list goes on!

As a computer science student, this is going to be an invaluable resource to you. Though it takes some time to get used to the commands, with some practice it offers you more power and speed than a user interface can offer. More importantly, we need it to compile our C code properly.

Once you start your second year courses, you will be expected to be using the command line extensively, so it's better to give yourself a head start!

---

## What command line should I use?
---
### Windows

If you're on windows, you have a bunch of options. By default, you should have `Command Prompt` installed. If you're using a recent version of Windows, you should also have `Powershell` available to you. These are both Windows-based, and are more than good enough for this course. Of these, I recommend using Powershell, since it has more commands available to you to make your life easier.


Additionally, you can also install the `Ubuntu Subsystem` which will give you a Linux-based terminal. This is a lot more powerful than the options above (and what you will be using in your upper year courses). You can find more information [here](https://answers.microsoft.com/en-us/windows/forum/apps_windows_10-winapps-appscat_books/how-to-access-your-ubuntu-bash-files-in-windows/201bb314-6b3a-4913-83b0-3d38037b9470) on how to access your files if you choose to use this option.

---
### MacOS / Linux

You should have a terminal installed by default, simply called `Terminal`. This is Linux-based, and plenty good enough for the rest of your university career. There are alternative terminals you can install - but I don't recommend going down that rabbit hole just yet - wait till you're more comfortable using it.

---

## Differences between terminals
---

Different terminals may have different names for commands that do very similar things. If you are using Command Prompt on Windows, some of these commands may have different names (I'm using a Linux-based terminal). 

Powershell should support all the commands here, as well as the ones from Command Prompt, which is why I suggest using it. When in doubt - Google is your friend!

---
## The Prompt
---

The prompt is the line that shows up when you open up a new terminal, and this is where you run your command. Here's an example of my prompt:

```sh
mustafa@xps:~/Desktop$ 
```

It usually consists of your username (mustafa), the name of the device (xps), and the current folder the terminal is in (Desktop). Your prompt may look different, but it'll usually have the same format as this.

---
## Getting around your files
---

The first thing you need to realize about using the terminal is that there is a concept of a 'current directory'. Much like the File Explorer, the terminal starts off in some directory. Pretty much all the time, you're going to want to be moving around different folders (for whatever reason). Here we'll talk about some commands that help you do this.

---
### pwd

The command `pwd` (**p**rint **w**orking **d**irectory) prints out the full path to the directory your terminal is currently in (called the working directory). For example, if I run the command while the terminal is opened on my Desktop

```sh
mustafa@xps:~/Desktop$ pwd
/home/mustafa/Desktop
```

*Note: Command Prompt doesn't have a nice equivalent to this. You can use `cd`, however this command is not meant for just this. More on this below.*

---
### ls

The command `ls` (**l**i**s**t) lists out the contents of the current (working) directory. You can provide it with the `-a` flag to also show hidden files, and also `-l` to show more information about each file.

```sh
mustafa@xps:~$ ls
Desktop       Downloads
Documents     Pictures
...
```
*Note: The equivalent to this on Command Prompt is `dir`*

You can additionally also give it the name of a directory, and it will list you the contents of it.
```sh
mustafa@xps:~$ ls Desktop
Folder1       Folder3
Folder2       Folder4
...
```

---
### cd

The command `cd` (**c**hange **d**irectory) lets you change the current working directory. This change will also be updated in the prompt.

```sh
mustafa@xps:~$ cd Desktop
mustafa@xps:~/Desktop$ 
```


