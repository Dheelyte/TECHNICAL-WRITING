---
title: "Introduction To Linux: Shell Navigation & Permissions"
seoTitle: "Introduction To Linux: Shell Navigation & Permissions"
seoDescription: "The purpose of this article is to show you how to navigate and manipulate the Linux File System."
datePublished: Thu Jul 13 2023 11:19:41 GMT+0000 (Coordinated Universal Time)
cuid: clk5k9dpi0jtefgnv1wtt2ffq
slug: introduction-to-linux-shell-navigation-permissions-968362aac6b9
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689519450960/c50ab82d-7ebd-4337-b810-3cdee64c4045.jpeg
tags: linux, bash, shell

---

Linux is a powerful, open-source operating system that was released in September 17, 1991. Apart from being open-source, Linux is the preferred choice for developers because it is easy to install, secure, stable, lightweight, flexible, and gives users more privacy. Linux is more than just an operating system. It is also used to run servers and embedded systems. Other examples of operating systems are Windows, MacOS and iOS. Even Android is powered by Linux OS.

It is important to note that Linux uses Bash, which is the most commonly used Command Line Interface (CLI) for Unix-based operating systems including Linux and MacOS. This means you can follow this article if you’re on Linux or MacOS. To install Linux on Windows, the easiest way is to use Windows Subsystem for Linux (WSL) which is as easy as running the following command on your CMD: `wsl --install`.

The purpose of this article is to show you how to navigate your Linux Operating System using its Shell. This involves learning how to navigate and manipulate the Linux File System; creating and updating files and directories, deleting and changing the permission to files and directories.

By the end of this article, you should know how to:

* Navigate in a Unix system
    
* List files and directories
    
* Create a file or directory
    
* Remove a file or directory
    
* Move or copy a file or directory
    
* Interpret and control access permissions to a file or directory
    

## **SHELL NAVIGATION**

A command is a program or utility that provides a function and runs on the Command Line Interface (CLI). We’re going to be looking at the following command and their functions: `pwd`, `cd`, `ls`, `touch`, `mkdir`, `cp`, `mv`, `rm`, `rmdir`, `echo`, `cat`, `man`.

### **pwd**

The first command we are going to look at is the `pwd` command. This command is used to display the path of the current working directory.

```bash
delight@DESKTOP:~$ pwd
/home/delight
```

Note that in the example above, the current working directory is the path after the colon and before the dollar sign in the example above. Also, the current logged in user is `delight` and the name of the computer is `DESKTOP`

### **cd**

To change our current working directory, we can use the `cd` command.

```bash
delight@DESKTOP:~$ cd first/
delight@DESKTOP:~/first$
```

To go back to the parent directory (the directory that contains the current working directory), add two dots in front of the `cd` command:

```bash
delight@DESKTOP:~/first$ cd ..
delight@DESKTOP:~$
```

### **ls**

The `ls` command is used to list the content - files and directories - of the current working directory.

```bash
delight@DESKTOP:~$ ls
notes.txt games/
```

To list the content in another directory, add the path to the directory in front of the `ls` command:

```bash
delight@DESKTOP:~$ ls games/
game1 game2
```

### **touch**

The `touch` command is used to create a file. The following example creates a new file with the name `new_file`:

```bash
delight@DESKTOP:~$ touch new_file
delight@DESKTOP:~$ ls
new_file
```

### **mkdir**

To create a new directory (folder), use the `mkdir` command followed by the name of the directory:

```bash
delight@DESKTOP:~$ mkdir new_directory
delight@DESKTOP:~$ ls
new_directory new_file
```

### **cp**

The `cp` command is used to copy files or directories to another directory. It can also be used to copy a file’s content to another file. Use the `cp` command followed by the name of the file/directory you want to copy and finally followed by the destination file/directory you want to copy to. The following example copies `new_file` into `new_directory`:

```bash
delight@DESKTOP:~$ cp new_file new_directory/
delight@DESKTOP:~$ ls new_directory/
new_file
```

As you can see by listing the content of `new_directory` folder, it now contains `new_file`.

### **mv**

The `mv` command is used to move or rename a file depending on how it is used. To rename a file, it is used like this:

```bash
delight@DESKTOP:~$ mv new_file renamed_file
delight@DESKTOP:~$ ls
new_directory renamed_file
```

Notice that `new_file` had been renamed to `renamed_file`. Also, if `renamed_file` existed, the content of `new_file` would be moved to `renamed_file.` To move a file/directory, it is used like this:

```bash
delight@DESKTOP:~$ mv renamed_file new_directory/
delight@DESKTOP:~$ ls new_directory/
new_file renamed_file
```

The `new_directory` folder now contains `renamed_file`.

### **rm**

To remove a file, the `rm` command is used, followed by the name of the file:

```bash
delight@DESKTOP:~/new_directory$ rm renamed_file
delight@DESKTOP:~/new_directory$ ls
new_file
```

The `rm` command can also be used to delete directories using the recursive option (`-r`):

```bash
delight@DESKTOP:~$ rm -r directory_name
```

### **rmdir**

This command is similar to the `rm` command except that it can only be used to delete empty directories.

```bash
delight@DESKTOP:~$ rmdir directory_name
```

### **echo**

The echo command is used to write contents to a file without using a file editor. The following example shows how to write the content `This is a file content` into a file named `main`:

```bash
delight@DESKTOP:~$ echo "This is a file content" > main
```

It is important to note that if `main` doesn’t exist, the `echo` command creates it, but if `main` exists, the `echo` command overwrites it. To append new content to a file replace the `>` in the example above with `>>` :

```bash
delight@DESKTOP:~$ echo "This is an additional content" >> main
```

### **cat**

To view the content of a file, use the `cat` command. The following example outputs the content of a file named `main`:

```bash
delight@DESKTOP:~$ cat main
This is a file content
This is an additional content
```

### **man**

The `man` command is a very useful command which every Unix user must know. It is used to display the detailed user manual of any Linux command. It contains the name, description and usage of a specified command. For example, to learn how to use the `mkdir` command, do this:

```bash
delight@DESKTOP:~$ man mkdir
```

## **SHELL PERMISSIONS**

Linux is a multi-user operating system. This means that multiple users can operate a Linux computer with multiple user accounts. A method was then devised to protect a user’s data from other users using the same computer; on a Linux system, each file and directory has an owner and a group (of related users). A file/directory can be accessible by either the user who owns the file and/or users in the group to which it belongs and/or everybody using the computer. This brings us to the concept of Permissions.

To view the permissions of a file or directory, we can list it using the `ls` command and a `-l` flag:

```bash
delight@DESKTOP:~$ ls -l
-rwxr-xr-- 2 delight students 4096 Jul 12 16:55 new_file
```

Let’s analyze what this means, shall we?

* The file `new_file` belongs to a user named `delight` and a user group named `students`.
    
* The first character `-` shows that this is a file (`d` indicates a directory)
    
* The next 9 characters indicate that this particular directory has the `rwxr-xr--` permissions.
    

What do these characters actually mean?

```bash
rwx                         r-x                         r--
user permissions     group permissions     all other users permissions
```

The first part indicates user (file owner) permissions to the file; `rwx` means the owner has rights to read, write and execute the file.

The second part indicates group permissions to the file; `r-x` means the group users can read and execute the file but do not have write permission to the file.

The third part indicates all other users’ permissions to the file; `r--` means that all other users have read permissions to the file but not write and execute permissions.

**Note that:**

* **r** means read permission (allows the content of the file/directory to be viewed)
    
* **w** means write permission (allows the file/directory content to be edited or altered)
    
* **x** means execute permission (allows the file to be executed or the directory to be entered)
    

### **Octal Notation**

Octal notation is a way of representing read, write and execute permissions using a set of octal characters which consists of a set of three numbers. Here’s how octal notation works:

```python
r = 4
w = 2
x = 1
— = 0
```

So, to represent a file/directory with permissions `rwxr-xr--` in octal form, we add their values together:

```python
r w x = 4 + 2 + 1 = 7
r - x = 4 + 0 + 1 = 6
r - - = 4 + 0 + 0 = 4
```

The first number (`7`) represents owner permissions, the second number (`6`)represents group permissions and the third number (`4`)represents the permissions of all other users.  
So a file with permission `rwxr-xr--` translates to 764 in octal notation.

In this section, we’re going to be looking at the following commands and what they actually do: `chmod`, `chown`, `chgrp`.

### **chmod**

The `chmod` command is used to control access permissions to a file or directory. To use it, we write the `chmod` command followed by the desired permission in octal notation and finally the filename.

```bash
delight@DESKTOP:~$ chmod 777 filename
```

In the example above, `777` represents the permissions of the file in octal notation. Note that `chmod` works the same way on directories as it does on files.

### **chown**

The `chown` command is used to change the owner of a file. To use it, write the `chown` command followed by the new user and finally the file name. To change the owner of a file, we must have **superuser privileges**. To enable superuser priviledges, our example employed the use of `sudo` command to execute `chown`:

```bash
delight@DESKTOP:~$ sudo chown mike new_file
```

The example above changes the owner of `new_file` to `mike`. Note that `chown` works the same way on directories as it does on files.

### **chgrp**

The group ownership of a file or directory can be changed using the `chgrp` command.

```bash
delight@DESKTOP:~$ chgrp new_group filename
```

It is important to note that you must be the owner of a file in order to change the file’s group ownership with the `chgrp` command.

### **CONCLUSION**

In this article, you were introduced to the Unix-based operating system, Linux and its advantages. We discussed how to navigate in a Unix-based system, list files and directories, create a file or directory, remove a file or directory and move or copy a file or directory. We also learnt about Linux permissions, how to represent permissions in octal notation and how to change the permissions of files and directories. Hence, you are now familiar with the Linux operating system.

Thanks for reading.

**Follow me on:**  
Twitter: [https://twitter.com/DelightGbolahan](https://twitter.com/DelightGbolahan)  
LinkedIn: [https://linkedin.com/in/delight-olagbuji](https://linkedin.com/in/delight-olagbuji)

### **REFERENCES**

[http://linuxcommand.org/lc3\_lts0020.php](http://linuxcommand.org/lc3_lts0020.php)

[http://linuxcommand.org/lc3\_lts0090.php](http://linuxcommand.org/lc3_lts0090.php)