# Training Materials for Linux
This repository holds training materials for ISU Linux Courses. This testing framework was developed by Barry Britt <bbritt@iastate.edu> for Linux Command Line training.

The idea for this was taken from nodejs training materials and adapted to use bash shell scripts.

## Requirements
- [bats (Bash Automated Testing System)](https://github.com/sstephenson/bats)
- [direnv (Environment Switcher for BASH)](https://github.com/direnv/direnv)
- Any recent Linux distribution

The **bats** program is available on Fedora and Red Hat Linux (and probably CentOS as well).

The **direnv** program needs to be compile from source and the executable placed into /usr/local/bin. After the executable has been placed, you should create a bash shim in /etc/profile.d that contains the line:

> eval "$(direnv hook bash)"

## Instructions
- Clone the repository
- Change to the desired directory (start with linux-1)
- read the example.*x* files, and try to do the exercises
- Check your work by running the bin/check*x* scripts.

## Scripts

### instructions
The instructions script reads the contents of files in the **.instructions/** directory. The files should be named **instructions.*label***, where label is some string of characters that will identify the target.

Instructions simply does a '**cat**' of the target file.

### check
The check script executes a **bats** formatted shell script named **check.*label*** in the **.bin/** directory. This is done to provide a consistent user experience when using the testing framework, since most (if not all) users will be unfamiliar with scripting and testing frameworks.

#### check.*label* scripts
The **check.*label*** scripts contain the tests that should be run to verify the instructions specified in **instructions.*label*** have been successfully carried out. Each test outputs a series of success or failure message to identify whether or not the instructions have been followed.

## Files

### *.envrc*
The .envrc file adds two variables to the users environment:
- **INSTRUCTIONS_PATH**
- **BINPATH**

These environment variables are used within the bash scripts.

### instructions.*label*
The instructions files only need to have the following string somewhere in the file:

> \# Title: \<your description here\>

The rest of the file can be formatted to your liking, but I have been using the following format:

> \#===== \
> \# Instructions \
> \# Title: Instructor Example 1 \
> \#=====
>
> For this example, you will need to use what we have learned today to create a file in the ~/examples directory named:
>
> test-1
>
>This file should contain, in reverse order, the top 10 lines from
    files/box-office-global
>
> \#===== \
> \# Checking your work \
> \#=====
>
Once you have created the file, you should 'cd' to ~/examples and type 'check ex1' to verify your work.


# Contact Information
Questions, comments, pull requests, etc... should go to
[bbritt@iastate.edu](bbritt@iastate.edu).
