---
title: UNIX Permissions Overview
sidebar: it_sidebar
permalink: it_permissions.html
folder: it
updated: 3/1/2016
---

Matt Peverill & Tara Madhyastha

# Permissions Basics

All files and directories have the same set of attributes (although what they mean varies slightly) between the two. You can see them easily by using the ls –l command. Here&#39;s a file and a directory:

 ![](data:image/*;base64,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)

The first, 3rd, and 4th column describe the permissions of the file.

The first column is the file permission block. We&#39;ll revisit it shortly. The 3rd
 column is the owner (mrpev in this case). The 4th column is the group.

Note that some permissions will also change the color of the file if you&#39;re using ls with color. Notably, a file which is executable will be green and a file which is opened up to all users will have a green background (usually bad).

## The File Permission Block

Here&#39;s how you read this:

 ![](data:image/*;base64,R0lGODlhCAJUAecAAP////7+/v39/fz8/Pv7+9rv99ju99fu9tXt9tPs9tLs9dDr9c7q9QAAAPn5+fr6+vX19fb29vf39/j4+O/v7/Dw8PHx8fPz8+jo6Onp6erq6uvr6+3t7fT09N/f3+Hh4ePj4+Xl5efn59PT09XV1dfX19nZ2dvb2+7u7vLy8sfHx8jIyMvLy87OztHR0dra2uTk5Le3t7q6ury8vMDAwMXFxcrKytDQ0NbW1t3d3aioqKurq6+vr7Ozs7i4uL+/v8bGxpeXl5ubm5+fn6SkpLu7u8TExM3Nzebm5omJiYyMjJGRkaenp7GxsXp6en5+foODg4qKipOTk5ycnG1tbXFxcXd3d39/f4iIiOzs7GJiYmdnZ3V1dYuLi6WlpVdXV11dXWNjY2xsbJCQkK6urr29vVFRUUtLS1BQUGFhYUdHR01NTVRUVF5eXmlpaYaGhpaWlqampra2tt7e3kREREpKSltbW3R0dJSUlLW1tdLS0kNDQ0hISFpaWmZmZnNzc6Ojo7S0tMPDw0FBQU9PT1hYWGRkZHJycoKCgpKSkkBAQEZGRk5OToGBgT8/P9zc3ElJSVJSUllZWWpqamVlZYSEhP///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////yH+Dk1hZGUgd2l0aCBHSU1QACwAAAAACAJUAQAI/gABCBxIsKDBgwgTKlzIsKHDhxAjSpxIsaLFixgzatzIsaPHjyBDihxJsqTJkyhTqlzJsqXLlzBjypxJs6bNmzhz6tzJs6fPn0AjBhhKtGhRAUiTKl3KtKnT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)

For regular files:

- Read means you can read the file and copy it
- Write means you can change the file
- Execute means you can run the file as a script or program.

For directories:

- Read means you can list directory contents.
- Write means you can create, rename, and delete files in the directory.
- Execute means you can enter the directories and access its contents.

There are some additional complexities here – you might see an &#39;X&#39;, &#39;s&#39;, or &#39;t&#39; in one of these positions especially for directories – but those are the basics. You can find more detail [online](http://unix.stackexchange.com/questions/79395/how-does-the-sticky-bit-work).

## What Ownership and Group Ownership mean

The owner and group ownership blocks describe who owns the file.

The file owner is usually the person who created the file. Importantly, only the owner (or a superuser) can change the permissions of a file or change the owner of a file.

You might sometimes see an owner that is just a number. Usually this means that the file belongs to a user that doesn&#39;t exist on the system and was copied from another system. Usually that is not what you want.

The file&#39;s group ownership just describes who gets the permissions from the file&#39;s group permissions settings.

## How to Manipulate Permissions

Changing ownership can be accomplished with the chown command. The syntax is:

chown OWNER[:GROUP] FILE

The group part is optional. Again: only the (individual) owner of the file or a superuser can change a files ownership.

To change file permissions you use the chmod command. The old school way to do this is to use an octal triplet to describe a combination of permissions in the permission block. This is still a good way to do if you want to set a bunch of files to have exactly the permissions you want, but most of the time using this syntax is easier:

chmod (u/g/o)(+/-)(r/w/x)

So to be clear:

- first describe whose permissions you want to change (user group or other)
- then describe whether you are adding or removing permissions
- then describe which permissions (r/w/x) you want to add or remove

# Knowing yourself – your user name and groups and umask

As you go around in the file system doing things, the files that you create will have certain permissions. What these permissions will look like has a lot to do with your own settings. Therefore, it is important to understand yourself before you accidentally create files that your group members cannot access.

You probably know your username (your netid) because you type it every time you log in. But if you forget, you can find out with a simple command:

```
#whoami
madhyt
```

So the owner of every file that you create will be set to your username.

But what groups do you belong to? You can find out:

```
#groups
madhyt map3 sls K_lab mrlang IBIC_RALLY udall ACT adni IBIC_core rtfmri retract nifd driving student ivan
```

Here you can see that madhyt belongs to sixteen groups. That is actually the maximum number of groups that you can belong to. If you are in 16 groups and need to belong to another group you need to be removed from another. Group membership is controlled by IBIC IT through a protocol called LDAP. Therefore, sometimes it takes some time (and you may have to log out and log back in) to see your new group memberships when they are added.

If you belong to multiple groups, what group is attached to new files you create? By default, it is the first group in that list. Notice that in the example above, the first (default) group is madhyt, the same as the user name. This is a group that includes just the one user, and it is set up that way to allow certain things to be easier (see IBIC Default Permissions for a detailed explanation of why).

You can change which group is your default group with the following command:

```
#newgrp ivan
ivan madhyt map3 sls K_lab mrlang IBIC_RALLY udall ACT adni IBIC_core rtfmri retract nifd driving student
```

However, this change is not permanent and will only affect the terminal that you are in.

There is a way to override the default group assignment to new files by changing the settings of the parent directory – specifically by setting the &quot;setgid&quot; bit. In the directory listing below, you can see that where the group execute bit would normally be, there is an &quot;s&quot; (highlighted in red). This setting on a directory means that all new files that one creates in this directory will be given the group of the directory (here, sls) rather than the default group of the person who creates the file. This is quite handy for preventing accidental group mistakes!

```
# ls -ld /project_space/sls
drwxrwsr-x 14 madhyt sls 16 2010-11-03 10:48 project_space/sls/
```

You can enable the setgid bit on a directory with the following command:

```
# chmod g+s /project_space/myproject
```

Finally, you need to know how the default file permissions block will be set when you create a new file. This is governed by your &quot;umask&quot;, which you can see using the following command:

```
# umask
0007
```

This is that old school octal code – but for most purposes human readable syntax is better. You can see what this octal code means by using the &quot;-S&quot; flag.

```
# umask -S
u=rwx,g=rwx,o=
```

This says that by default, the user and group will have read, write and execute privileges, but other (everyone else) will have no access to the file whatsoever.

# Example Recipes for Consistently Using Permissions

The previous section should have convinced you that UNIX permissions are not the easiest thing in the world to deal with. Therefore, we have described some strategies for managing permissions to achieve certain goals.

## Proposed Permissions For IBIC/Multiple Project Shared Lab

Our goals for permissions are:

- People should be able to easily work on multiple projects without accidentally creating files that other people can&#39;t read.
- People should be able to protect their data from other members not in the project.
- By default files that people create are private.
- We would like to keep permissions simple.

The tradeoffs we are willing to make are:

- There is no &quot;tiered level&quot; of permissions – you either have access to a project or you do not.

What things look like on the file system:

- Most things should be rw\_rw\_r\_\_.
- Scripts should be rwxrwxr\_x.
- Data files should be r\_\_r\_\_r\_\_ so we don&#39;t accidentally delete them.

Ownership should work like this

- Each project has its own associated group.
- Files within a project folder can belong to any member of the group.
- The setgid bit should be set at the top level of the project, so that all files that are created within the project directory belong to the associated group.

What things look like for the user:

- Umask should be set to 0007
- Users default group should be the same as their netid (the group of one&#39;s self)
- The default group should be the group of one&#39;s self

Group Membership should work this way:

- People should belong to their default group of one&#39;s self and all other groups that are associated with projects that they belong to.

- At least a few people should have sudo privileges  to be able to resolve weird permissions problems.

## Proposed Permissions For the Stress and Development Lab

Our goals for permissions are:

- People can change whatever about their own projects, but should be protected from deleting data.
- Basic users can log in and read things, and make changes in specific folders, but can&#39;t modify other stuff.
- Advanced users can change most things, but are protected from deleting data.
- We would like to keep permissions simple

The tradeoffs we are willing to make are:

- Everyone (people not in our lab) can read everything – there is no protected data
- By default files that people create are _not_ private though they can make them so.

What things look like on the file system

In general things should be set up in this way in our data directory:

- Most things should be rw\_rw\_r\_\_.
- Scripts should be rwxrwxr\_x.
- Data files should be r\_\_r\_\_r\_\_ so we don&#39;t accidentally delete them.

This is because we don&#39;t want people outside the lab modifying things if our share is mounted from other machines.

Ownership should work like this

- Files within a project folder should belong to the project lead so that they can manipulate everything in their directory.
- Most files should belong to the sdlabadmin group.
- Files we want more people to edit (like Freesurfer files being actively edited) should belong to the sdlabbasic group.
- The setgid bit should be set accordingly on these directories.

What things look like for the user:

- Umask should be set to 0007

- The default group should be the highest privilege group


Group Membership should work this way:

- People who know what they&#39;re doing should be in sdlabadmin and sdlabbasic. Their default group should be sdlabadmin.
- People who don&#39;t know what they&#39;re doing should be in sdlabbasic only
- At least a few people should have sudo privileges to be able to resolve weird permissions problems.

