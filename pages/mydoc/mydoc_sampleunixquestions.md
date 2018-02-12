---
title: Sample Unix Questions
sidebar: mydoc_sidebar
permalink: mydoc_sampleunixquestions.html
folder: mydoc
---

This is a set of questions that you can use to test your knowledge of UNIX concepts. 

## Basic UNIX Commands

Give a command to copy file a to file b (do not use file redirection)

Give a single command to count the number of words in the document mydoc.

You are in the directory /var/tmp. How can you cd to your home directory? Give
three ways of typing this command. What is the shortest number of characters you can type that will get you home?

How can you find all lines containing the text “dim” in a file called “fslheader.txt”?

Give a single command to create a directory ~/foo/bar/baz

There is a dictionary of English words in /usr/share/dict/words. What command would you use to find out how many words begin with a lowercase “b”?

What command would you use to find all the words that contain two consecutive a’s? (e.g., “aa”, “Aa”, “AA” or “aA”?)

How would you use the command “cp” to copy a directory in your home called badsubjects/ica to /var/tmp? Do the timestamps on these files change when you do this copy? How did you check the timestamps?

How can you perform this copy keeping the timestamps the same?

How could you use the command “tar” to perform this copy? When would this approach make really good sense?

Give a command to display the first three lines in your .bashrc file on the terminal.

Give a command to display the last 10 lines in your .bashrc file on the terminal.

How would you print all but the first line of your .bashrc file?

How can you remote-login to another computer (e.g., you are on your desktop workstation and you want to log on to broca?)

How can you remote-login to another computer from your Linux desktop (Gnome) so that you can open fslview from the other computer?

Challenge. What is the IP address of precuneus? How did you find out?

Challenge. Suppose you get a timeout logging on to broca. Maybe the heat in the machine room got to be too much and the machine crashed. Alternatively, perhaps it is incredibly slow because the NAS is full and you just can’t log in. Your life is miserable either way but maybe there is hope. What command can you issue to determine if it is still alive?

How can you tell whether a directory is local to the computer or on another computer or on NAS1 or NAS2? Why does knowing this make a difference?

Your machine is running slowly. Give at least two commands you can run to see why?

Someone told you to use the FSL command fsl_sub. Give a command to find this executable in the file system.

Give a command to determine what kind of file it is. Is it a shell script?

Give a command to page through it.

Challenge. Give a command in one line to page through the command while in your home directory, without specifying the path. [ Hint: google UNIX backquotes]

Give a command to find out how much disk space you are using in your home directory, sorted from biggest file or directory to smallest. Can you print out sizes in MB?

You are working on files in two directories – a project directory and a directory with data files. Explain how to use pushd and popd to move between them.

You have two files of subject identifiers. The first contains a list of all the subjects. The second contains a list of the subjects for whom a certain analysis completed. How can you obtain a list of all the subjects who have NOT completed the analysis? [ Hint: grep ]

## Permissions

Look at this listing from the ls -l command.
```
drwxr-xr– 4 root root 0 Dec 19 15:08 projects
```

Is projects a file or a directory? Can you cd into it? Why or why not? Who or what is root?

How can you tell what groups you belong to?

How can you tell what groups someone else belongs to?

If you and your friend belong to a common group called “digit”, how would you set the permissions on a directory called “foo” so that you both can read and write files in that directory?

Write the 9-character permissions, owner, and group of this directory.

Challenge. What if you and your friend have no groups in common. Your system administrator is gone – you can’t ask him/her to create a group.

How can you set up permissions on a shared directory, called “bar”, so that you and your friend can read and write files in that directory?

What are two directories that you can count on to create temporary files? What is a command that you can use to generate a unique temporary file name?

Why is it a bad idea to create a file called /tmp/foo?

## Wildcards

The UNIX command wc counts the number of lines, words, and characters in a file. How can I use this command to count all the lines, words, and characters
in all files in the directory /usr/foo?

Give a single command to count the number of lines in all the files ending with “.h” in /usr/include.

Give a command to echo all files that begin with the letters “RC4”.

Give a command to do a directory listing of all directories that end with a digit (0-9).

Give a command to remove all files and directories that begin with the characters “tmp”.

## Pipes

Give a command that uses a pipe to page through a long directory listing.

Give a command that uses a pipe and “cat” to print the first 5 lines of a file.

You are in a directory full of subject data directories, with names:
```
S1001
S1002
S1003
…
S2001
S2002
S2003
…
```

There are many many subjects; so many that you cannot see them all on the terminal. How can you list the contents of each directory recursively and look at
that by paging through?

These subjects are in two groups (S1??? = Parkinson’s disease and S2??? = healthy controls). Give a command to count the number of subjects.

Give a command to count the number of subjects with PD (hint: need to understand wildcards).

Give a command find the number of files in the directories of subjects with PD.

Describe how to use a pipe to view only the first few lines of the output of the command “flirt”, which by default is a help message.

You have a spreadsheet with columns “Subject”, “ParcelName”, “Volume”. These columns are separated by TAB (\t) characters. For each subject there are 50 parcels, so the information in the Subject column is repeated many times.

Give a command to count the number of unique subjects in this file.

You have a file with a list of subject identifiers that include a timepoint and a three digit number:
t1_001
t2_001
t1_002
t2_002

Use cat, sed and uniq together to generate a list with the subject identifiers
alone and repeats removed:
001
002

## Standard Input/Output

The command tee <filename> copies its standard input into filename. Explain
how to use tee to put the output of a command to a file called MAKELOG. Remember that commands may write output to both stdout and stderr.

How in bash can you redirect stdout and stderr to a file? Give an example.

How in bash can you redirect only stderr to a file?

The command "antsIntroduction.sh" (find it if you don’t know where it is – it is part of the Advanced Normalization Tools package) can be called with the -h option to get help. Why doesn’t it work to pipe this through more as follows?

```
antsIntroduction.sh -h | more
```

How should you revise the above command to work as expected, and explain why.

## Redirection

Use file redirection to put the listing generated by ls into a new file called
/tmp/foo.

Use file redirection and cat to print the contents of file /tmp/foo.

Use cat and file redirection to create a file called baz with the contents:

```
a
b
c
```

Now add a line with a “d” to that file.

## Job Control

How can you suspend a job that is running? For example, start emacs at the terminal window. How do you get the prompt back?

How can you now run that same emacs window and use your terminal window at the
same time?

If you know you want to start emacs and still maintain your shell, how can you
run emacs in the background from the beginning?

If you start some program that seems like it will be running a very long time,
how can you kill it?

How can you see what job is taking up the most CPU and kill it? When can you actually kill someone’s job? How can you tell whose job is whose?

## Practicing With FSL Commands

You have an image that has p values (0 through 1). How can you use fslmaths to
convert these to 1-p, so that .05 becomes .95?

## Shell Scripting

Copy /project_space/makepipelines/oasis-multisubject-sample to your home directory. Make all changes to this copy; don’t edit the originals! Write a bash shell script to reorient each of these images (using fslreorient2std) and skull strip it (using bet). Hint: This will involve a loop over the subjects, and your program should not include the actual list of subjects.

Copy /project_space/makepipelines/oasis-longitudinal-sample-small to your home
directory. Make all changes to this copy! Write a script to produce a comma separated value file with two columns: the first is the subject identifier (SUBJID) and the second is the number of visits that they have completed (NVISITS). The comma-separated value file should have these two column names as headers.

Now let’s go one step further. Write a script to determine whether any of these subjects are missing a visit between their first and last visits. For example, if they came for visit2 and visit4 only, they would be “missing” visit 3.

Hint: How did you test this program to see if it works correctly?

Write a shell script that will calculate the size of a NIfTI file when uncompressed.

Some glitch in the way data were converted from DICOM resulted in a bunch of resting state NIfTI files having the .nii.gz extension when they should have had the .nii extension (in other words, they were not compressed using gzip). Write a program to find which of those files are affected and correct the problem. Each is named rest.nii.gz within a subject directory.

{% include links.html %}
