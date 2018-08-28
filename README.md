# CPSC 120 - Lab 01

The purpose of this lab is to get familiar with the UNIX system,
[Tuffix](https://github.com/kevinwortman/tuffix), and GitHub. As part of the
lab, you will get to compile and run the HelloWorld program.

## Goals

* Use Tuffix, and get familiar with the UNIX system.
* Clone a GitHub repository.
* Compile C++ source code and execute the compiled code.
* Edit C++ source code.
* Commit your edit and push it to the GitHub repository.

## Background

### UNIX system

You might be familiar with operating systems like Windows or macOS. UNIX is another operating system that was developed back in 1969 by AT&T Bell labs. Operating systems manage the computer resources such as the memory, hard-drives, keyboard, mouse, screen, etc. For example, whenever you are copying a photo from your camera SD card connected to your computer to the computer's hard-drive, the operating system is taking care of performing this action in the background.

Many operating systems have been developed as an extension, or very similar to the UNIX operating system. Some of these are Linux or macOS.

#### The UNIX Shell

There are many ways to interact with an operating system: you can see the visual screen of your phone and interact with it by touching it, or you can listen to a Google Home device and interact with it by talking to it. One of the most basic ways to interact with an operating system is by using the UNIX shell, which looks like this:

```bash
luislarco@mylaptop:~$
```

The UNIX shell is a program that expects the user (you) to input commands (using a keyboard in most cases) and then sends your commands to the operating system to be executed on your behalf. There are multiple types of UNIX shells which determine the format/style of commands it expects. In this class, we will be using the *Bash* UNIX shell.

### Git, GitHub & GitHub Classroom

When writing code for a program, it is extremely helpful to keep track of the changes that you have made to your code. Sometimes you realize that a piece of code you recently wrote is actually broken and you need to revert it to an older version. A software that allows you to keep track of your code changes is called a version control system.

In addition, when working in a project with multiple people, programmers might need to update the same file at the same time. A **distributed** version control system allows each member of a team to download a copy of the existing code so that they can work on it locally, and later integrate it with the code from other members of the team. This allows the team to implement a software faster.

Git is a free and open source distributed version control system and is widely used in academia as well as the industry. GitHub is a web-based service that provides an online server to host code online that can be updated using Git. You can think of GitHub the same way you think of Dropbox, but made specifically to integrate with the Git system.

GitHub Classroom is a service that GitHub offers specifically designed for implementing Git in a classroom environment, where students download some code, implement their assignments, and then submit the code through Git, allowing the instructor to see all the submissions. We will be using GitHub classroom in all of the coding assignments of this class (labs and final project).

Git is a extremely powerful tool that allows teams to work on multiple versions of code, and because of this, Git can also get very complicated. For the purposes of this course, we will be learning three basic Git operations that will allow you to submit your assignments:

1. `git clone`, which allows you to download a copy of the code stored in GitHub onto your local computer so that you can edit it locally.
1. `git commit`, which is used to store (or save) a current version of your code (think of it as clicking the save button on a document you are editing).
1. `git push`, which uploads all of the versions you have stored each time you execute `git commit`. You can *commit* your code multiple times, creating multiple versions of your code. For these assignments, we will always only grade the most recent *commit* of your code (which is the most recent version).

We will show you how to use the commands listed above in the lab instructions.

## Pre-requisites

For this assignment, you must have a GitHub account linked to your university email.

If you have never had a GitHub account, you can create one by visiting the [GitHub](https://github.com/) website and filling up the form to sign up for GitHub. Make sure to use your university email when creating the account.

If you already have a GitHub account, but it was created using a different email, you need to link your GitHub account to your university email. Log into your account on the GitHub website and then visit the [Email settings](https://github.com/settings/emails) page to add your university email. Once you add your university email, you will receive an email which will allow you to verify that the email belongs to you.

## Lab instructions

### Cloning the Git Repository

One you are logged into your GitHub account, open the assignment URL that your instructor has shared with you. It looks like this: https://classroom.github.com/a/some_random_code

After opening that link, GitHub will generate the your own repository that will contain the starter code of the lab. This is the same repository where you will be pushing (submitting) your code for grading. Once the repository is generated, a similar message will show:

> Your assignment has been created here: https://github.com/CSUF-CPSC-120-LW/lab-01-your_user_name

Open the link to see the web-view of your GitHub repository. In there you will see two files:

1. `README.md`: an exact copy of the file you are reading right now.
1. `helloworld.cc`: the starter code for your lab assignment.

Now we need to clone your repository into your local computer so that you can start working with that code. To keep your files organized, we will first create a folder for this class, and in that folder we will clone your repository.

#### Creating a folder

By default, opening a terminal (or ssh'ing into the university's computers) will take you straight to your home directory, which is usually referred as `~`. If you are using Tuffix, the location of your home directory is `/home/your_user_name` (you can check by running the `pwd` command).

Let's go ahead and create a folder in your home directory called `cpsc120` by running the following command:

```
~$ mkdir cpsc120
```

After you press enter, the folder cpsc120 will be created, which you can verify by listing all the files and folder under your home directory:

```
~$ ls
cpsc120 Desktop Documents ...
```

#### Accessing the folder (changing a directory)

Now, let's enter the folder so that you can clone your repository inside. We are going to use the `cd` command, which stands for *change directory*:

```
~$ cd cpsc120
~/cpsc120$
```

You can notice now that, right before the `$` sign, the directory is now `~/cpsc120` instead of just `~`.

#### Cloning the git repository

Now we are ready to clone your repository. Go back to the web-view of your GitHub repository and click on the **Clone or download** green button on the top right, and then click on the copy button right next to the repository address. Then, go back to the terminal and run the following command:

```
~/cpsc120$ git clone <paste repository URL>
```

The command will ask you to input your GitHub username and password. Once you enter that information, the repository is then downloaded (cloned) into your computer. The whole process will look similar to this:

```bash
~/cspc120$ git clone https://github.com/CSUF-CPSC-120-LW/lab-01-your_user_name.git
Username for 'https://github.com': your_user_name
Password for 'https://github.con':
Cloning into 'lab-01-your_user_name'...
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 1), reused 9 (delta 1), pack-reused 0
Unpacking objects: 100% (9/9), done.
```

Now you can notice that there is a new folder called `lab-01-your_user_name`:

```
~/cpsc120$ ls
lab-01-your_user_name
```

Let's access that folder and look at the contents:

```
~/cpsc120$ cd lab-01-your_user_name
~/cpsc120/lab-01-your_user_name$ ls
README.md helloworld.cc
```

As you can see, a copy of the two files that you saw on the web-view of your GitHub repository have been downloaded (cloned) into your computer. You have successfully cloned your lab assignment's git repository.

### Compiling and executing code

The file `helloworld.cc` contains source code for the HelloWorld program, written in C++. HelloWorld is a program that prints "Hello World!" in the terminal whenever it is executed. As you will learn later in the class, source code must first be compiled so that it can be executed in the computer. Let's go ahead and compile the source code.

#### Compiling source code

Tuffix comes with the `g++` compiler installed. Let's take a quick look at the contents of that file using the `cat` command, which prints the contents of the file in the terminal. Run the command `cat helloworld.cc`:

```
~/cpsc120/lab-01-your_user_name$ cat helloworld.cc
// HelloWorld program
#include <iostream>

int main()
{
  std::cout << "Hello World!\n";
}
```

To compile the `helloworld.cc` source code, run the following command:

```
~/cpsc120/lab-01-your_user_name$ g++ helloworld.cc
```

Now you will see that a new file `a.out` has been created:
```
~/cpsc120/lab-01-your_user_name$ ls
a.out helloworld.cc README.md
```

This file is the compiled version of the source code, which we call a binary file (you will learn more about this later). This file is also an executable file, which means that we can run/execute it. Let's go ahead and execute the code.

#### Executing code

To execute or run the code, you need to append the prefix `./` to the name of the binary file. Type `./a.out` in the terminal and press enter. That will run the code and print any outputs that the code generates. It should print the following:

```
~/cpsc120/lab-01-your_user_name$ ./a.out
Hello World!
```

Now you have successfully compiled and executed C++ code!

### Editing code

*TODO(llarco): Complete this section.*

### Pushing code to Git (submitting your assignment)

*TODO(llarco): Complete this section.*
