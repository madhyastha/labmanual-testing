---
title: The Programmer's Guide to Being Awesome & UNIX Cheat Sheet!
author: Maya Reiter
sidebar: mydoc_sidebar
permalink: mydoc_unixbible.html
folder: mydoc
---
By Maya Reiter

# Introduction
To open a terminal click: **Applications -> Accessories -> Terminal.**

First of all, you should know that **in Unix, capitalization matters**.
Always.

Thus, “apple” is different from “Apple” and “ApPlE” and “APPLE” etc.

**Consult google and the Unix man pages (or me (: ) *when* you need
help!**

-   **What is google? - duh.**

-   **What are the Unix man pages? -** The unix man pages are the
    official manual and documentation of all the unix tools available.

    -   **Type “man ls”** in the terminal and it will take you through
        the help manual for the **ls** command.

    -   I find the man pages confusing. I often can’t understand them.

    -   Hence the google option. Never fear, a nerd has already answered
        your question on google. Stack overflow is usually good at
        answering programming questions.

    -   As time has gone by, I have gotten better at reading the
        man pages. This is encouraging.

# Now for the good stuff!

**In windows, we click (or double click); In Unix, we type *(we touch
type)*. **

(if you can’t touch type, you will soon be able to)

## Getting around without clicking:

### List the files in a directory:

**ls:** list at all the files.

**ls -l :** list at all the files, permissions and last
        edit time.

**ls -1:** list all the files, one per line

**ls -a:** include hidden files.
**ls -F:** see file types.

### Going places:

**cd /my/desired/location:** changes directories to
        desired location.

**cd -** go to your home directory.

**cd ~ :** go to your home directory.

 **cd .. :** go up one directory.
 **cd ../.. :** go up two directories.

**pushd . :** bookmark my current location.

**popd :** go to my bookmarked location.

### Reading things:

 **cat file.txt: “**print” a file to the terminal.

  **tac file.txt:** “print” a file to the terminal back to front -
        good for seeing the last line first in a long file.

  **more file.txt:** scroll through a file.

   **less file.txt:** scroll through a file (going
        backwards allowed)

  **head -n 7:** print the first 7 lines of a file.

   **head -n -7:** print all but the last 7 lines of a file.

  **tail -n 7:** print the last 7 lines of a file.

   **tail -n -7:** print the file starting from the 7th line.

## Handling files:

### Making things: 
NOTE -do not use special characters ever in file names.

  **touch file.txt:**

  **emacs file.txt:**

  **gedit file.txt:**

 **mkdir -p directory1/directory2/directory3:**

### Copying things:

   **cp file.txt /location/**

  **cp -r directory.txt /location/**

### Moving things:

 **mv file/directory /location:**

### Removing things 
PROCEED WITH CARE:

   **rm file:doit**

  **rm -r directory:** please do not remove any directories for  a while.

        -   are you scared? good!

        -   Just kidding, but you do need to realise the power of
            your command.

        -   You could delete all the data! (It is backed up, but lets
            try to not go there)

### Permissions:

   **Changing groups:**

   **Changing permissions:**

   **Adding sticky bits:**

### Unix tools:
You are not the master until you learn these tools.

If you can’t understand the **man** pages I would highly suggest
googling and trying out all of these things:

   **echo “Hello World” -** prints hello world to the terminal.


   **grep -** filters things for that you print.

   **sed -** will replace things for you.

   **awk -** will let you print specific fields of your data (columns)

   **find -** will search.

   **diff -** will compare two files for you and show you where
    they differ.

   **bc -** Doing math is easier in bash scripts if you pipe it
    through bc.

   **cut -** Tool for chopping up strings.

   **uniq -** gets rid of duplicate things.

   **sort -** sorts things for you.
   **Paste & Transpose**

## Piping:

   **how? **

    -   In Unix you have the option of chaining together
        several commands. This is called “piping”. the pipe (“|”) allows
        you to string together two or more commands.

   **why?cat**

    -   Unix/Linux was developed with the goal of enabling users to
        execute very powerful commands. (and why shouldn’t we be able to
        do EXACTLY what we want?)

   **when?**

    -   For example: Lets say I want to list all of the directories with
        a .gfeat extension:

        -   ls | grep .gfeat

            -   ls gives you a list of all the files in your
                current directory.

            -   the grep command then filters that list, showing you
                only the ones that are gfeat directories.

    -   Another example: I want print a script to the terminal and
        replace all instances of “Year1” with “Year2”.

        -   cat script | sed ‘s/Year1/Year2/g’

            -   cat script prints the script to the terminal.

            -   the sed command then replaces all the Year1’s
                with Year2’s.

    -   The list of possibilities available to the crafty Unix user is
        truly vast. For the most part, if you can do it at all, you can
        do it in one command.

## Calling scripts:

## How:

   **Calling a script:** one calls or “executes” a script by
        inputting the full path or location of the script in the
        terminal and hitting return (enter).

        -   example: /Where/my/script/is/myScript\_doThings.

   We have just successfully called our myScript\_doThings script.

   What things is this script going to do?

   This brings us to the topic of 

### Arguments

An argument or parameter is an instruction “passed” to the script that
tells it “what type of thing to do”.

We “pass” arguments to scripts in this manner:

```
./myScript_doThings **thing1**
```

(thing1 is our “argument”)

   Now our script knows that it should be doing “thing1” (what ever
    that may be).

   If we told it to do “thing2”, we would get different **Output.**

**Output is the result occurring from calling a script. Output is
dependant on “*input”***

**Input is the list of arguments passed to a script.**

Thus, as we have seen, the output of the myScript\_doThings script will
depend on the input (or the argument) we passed the script. The output
of myScript\_doThings thing1 **!=** the output of myScript\_doThings
thing2.

**!= means “does not equal”**

**== means “is equal to”**

## Lets talk about Variables:

Computers are idiots. The know nothing at all, in fact, there are 2
reasons they are better that humans at doing some things:

1.  They are fast - why they are fast is beyond the scope of
    this document.

2.  They never forget - they never forget because they use
    **variables**.

*** A variable is a unit that stores something.***

-   a “variable” in “computer” is the same as a variable in algebra.

    -   x = 2

    -   y = 3

-   We use variables to store information.

-   information in variables is never “forgotten”

-   Unless it is overwritten.

Putting information into a variable is called “**assigning**”. We
assigned the variable “x” to store the information “2”. What is x? x is
“2”.

We use the “=” sign to assign variables.

***the “=” sign* != *the “==” sign.***

***In english we use the two synonymously; we always use the word
“equals”. But remember, computers are stupid and they can't tell the
difference. So they need to use different vocabulary.***

***In computer: = equals “is”***

***== equals “ is equal to”***

***The computer to english translation of equal signs.:***

### Computer English

**x = 1 x is 1**

**1 == 1 1 is equal to 1 **

To illustrate how stupid computers are I will describe a scenario and
show you how a computer would understand it.

***scenario (english):** A boy meets a girl he likes and asks her out
for dinner. She decides she likes him and accepts his offer.*

***scenario (computer):***

***\#** a computer will ignore everything after a pound sign.*

*\#boy sees girl*

**boyLike = “yes”.**

**\#**girl sees boy.

**girlLike = “yes”.**

**if boyLike == “yes”**

**ASK HER OUT.**

**\#**boy asks girl out because he likes her.

**if girlLike == “yes”**

**GIRL ACCEPTS INVITATION.**

**answer = yes.**

### Scripting:
Now that you know many unix commands and some programming
lingo, it is time to talk about scripting.

**A script or a program is a file containing commands for the computer
to execute.**

-   We use scripts when we need to execute many commands one after the
    other, and when we would like to “keep” these commands for
    future use.

### Important aspects of writing scripts:

* Writing readable code:  have you ever tried to read instructions
written by somebody else and found them to be illegible? Have you ever
tried to read instructions you had written yourself a long time ago and
thought “WHAT WAS I TRYING TO DO?”. These situations are very
frustrating and can turn a 5 minute task into a 5 hour task.

A script should be written such that anybody can read it quickly and
understand what the script is doing, how it is doing it and how to run
it.

* How is this accomplished?

-   **Documentation -** you should always keep documentation of any
    scripts that you write, in case you or one of your co-workers needs
    to use it. The ibic wiki is the best place to document scripts, but
    a google doc is also a good option.

    -   Document the name and location of the script - if you can’t find
        it, it doesn’t exist.

    -   Document what the script does - what the output of the
        script is.

    -   Document the input of the script - how to run it.

-   **Comments -** The documentation described above serves the purpose
    of describing how and why to ***run*** the script.

**Comments in the code serve the purpose of describing how you got the
script to do what it does.**

Comments are good because the let other people see what the code is
doing. If a script needs to be modified for the use of another group,
project or task, comments allow easy modification. Modifying a script
with no comments takes as long as writing a new one.

**How to make a comment inside code?**

**A computer will read anything written on a single line after a “\#” as
a comment.**

Computers will not execute comments.

Note, comment signifiers are different in every language.

google: how to comment in language zYXLP to find out how to comment in
desired language.

**How to comment well?**

-   **Every script should contain a comment describing:**

    -   What the script does.

    -   What the usage of the script is.

    -   What the input/s of the script is/are.

        -   --Trust me, you will not remember how to call your
            own scripts. And you will want this information.

-   **Every sub-section should have a comment describing what the
    subsection is doing:**

    -   Segment your scripts into subsections. Have a subsection where
        you assign any variables you plan to use.

    -   If you are doing separate tasks within the same script, specify
        when you are executing which task.

-   **Resist the urge to “over-comment” -** in general, comments should
    specify “what” the code is doing and not go into “how” the code is
    doing it.

    -   When programmers want to know “how” the code works - they will
        read the code under the comment - so long as you write the code
        in a readable way (more on this later).

    -   If you comment out code during testing - remove it when you
        are done. it is confusing.

    -   Do not make comments overly long - if you have a multi-sentence
        comment, you probably haven't divided your code into small
        enough sub-sections.

**How to make your code readable:**

-   **Good variable names:** I can’t stress this enough: variables store
    information, if you give variables names that don’t pertain to the
    actual information stored, you are in for a world of pain.

    -   never use numbers or letters as variable names. 1,2,3,x,y,z
        -these are meaningless.

    -   If your variable name is a multi-word, begin each new word with
        a capital letter.

        -   ex. - variableName.

    -   Don’t make your variable name too long either -

        -   ex - thisIsABadVariableNameForAVariable.

-   Example of bad variable naming:

\# This code will illustrate bad style: You remember this example from
before:

*\#* This code is in **“pseudo code” **

**pseudo code is code that won’t actually work and is written either for
demonstration purposes or to organize one's’ thoughts before they embark
on the joyful task of finding the correct syntax for desired command.**

\# It is a compromise between “English” and “Computer.”

**Bad code example:**

\#there is no comment to tell me what the code should do :(

**a = “yes”.**

**b = “yes”.**

**if a == “yes”**

**ASK HER OUT.**

**an = “maybe”**

**if b == “yes”**

**GIRL ACCEPTS INVITATION.**

**an = yes.**

**What does this code do and why?** It is very hard to tell because it
is written in such bad style.

\#Example of better style on next page: (see if you can tell why the
second version is better)

\#This code describes the process by which a girl got asked out by a
boy.

\#assign variables:

**boyLike = “yes”**

**girlLike = “yes”**

**girlAnswer = “maybe”**

\#boy’s decision:

**if boyLike == “yes”**

\#code for boy ask girl out.

\#girl’s decision:

**if girlLike == “yes”**

**girlAnswer = “yes” **

\#code for girl replying affirmatively.

**\***you may notice that in addition to nice variable names and
comments, the second block of code is spaced out nicely.

-It uses consistent spacing between the subsections.

-It uses consistent indentation.

**Programming Constructs:**

**A programming construct is a basic element, command, or statement used
in various programming languages.**

Programming constructs are “concepts” that can be utilized in any
programming language. For example, **a variable is a programming
construct**. If you are writing in Bash/Java /Python /C or any other
language, you will be able to assign variables.

The difference between assigning variables in Java vs Python is purely a
**syntactic** one.

**Syntax is the particular way a programmer writes code to employ a
programming construct in a specific programming language.**

For example, here is the **syntax** for assigning a variable in bash:

**bashVariable= ”my bash variable”**

This is different from assigning a variable in python:

**pythonVariable = “my python variable”**

\*the difference is that bash won't allow a space between the variable
and the “=” sign.

R doesn’t use a “=” sign at all:

**RVariable -&gt; “my R variable”**

As you can see, in all these languages you can use variables to store
information, however, each language has different **syntax** that you
must follow. (much like human languages).

**Programming construct \#0 - Google knows everything.**

so if you don’t know it, google it. or bing it.

*don’t be a bigot, bing it!*

The internet if full of nerds and programmers with questions that are
the same as yours.

If you don’t know how to print only the first word of every line of a
file in bash, you should google:

***How do I print only the first word of every line of a file in
bash?***

**Programming construct \#1 - Loops**

Most everything you want to do multiple times in a program you will do
in a loop.

**A loop executes the same command/s over and over until it receives an
instruction to stop**

**There are two types of loops in “computer”**

-   **For loops -** For loops are the most commonly used loops. THEY ARE
    SO USEFUL!

To illustrate what a for loop does, I will give you a metaphor:

**For** each **student** in the **list of students** on the attendance
sheet:

The teacher will call the student’s name.

**alternatively, we could write:**

teacher calls name of student a.

teacher calls name of student b.

teacher calls name of student c.

teacher calls name of student d

…

teacher calls name of student z.

But what if the teacher were teaching psych 101 at UW? there are 720
students in that class!

--As you can see, loops are awesome, start getting excited, the future
is wild.

-   **While loops -** While loops execute a series of commands over and
    over **while** a predefined statement is True.

To illustrate what a while loop dues, I will give you a metaphor:

**While** you are gone:

I will read my magazine for 10 minutes.

then I will take a 10 min walk.

In this example, what a while loop does in this situation is as follows:

1.  while loop checks if you are gone: (you are)

    1.  I read my magazine for 10 minutes

    2.  I take a 10 min walk

2.  While loop checks if you are gone (still gone)

    1.  I read my magazine for 10 minutes

    2.  I take a 10 min walk

3.  While loop checks if you are gone (You returned while I was on
    my walk)

4.  While loop is now done.

**Beware the infinite loop!** If you are using while loops, and your
program appears to be stuck, you may have written an infinite loop!

Consider what would happen in our previous example if you NEVER came
back!

--I would have forevermore read my magazine for 10 minutes and then
taken a 10 min walk.

**Forever. **

**--** This is because the statement “you are gone” is always true. This
might seem like a silly example, but it happens, believe me.

example of a mistake that lead to an infinite loop:

**While 1 == 1**

**do something**

**do something else**

**do something other.**

As you can see 1 is always equal to 1. And so this loop is the loop that
never ends, it just goes on and on my friends, some people started
coding it not knowing what it does, and they’ll continue doing it
forever just because this is the loop that never ends…..

**Programming construct \#2 - Conditionals**

**Conditionals are a way to give the computer some criteria by which to
make decisions.**

Computers are black and white, they take everything literally and have
no judgement, sentiment, or conscious; they do not lie and they are
always right. GET USED TO IT.

Many times we want to execute commands (in a loop or not in a loop),

> but only **If something is true. **

In the real world we are faced with conditionals every day.

**If** it is the weekend

I want to sleep in

**If** it is not the weekend

**if** it is not a holliday

My alarm needs to go off at 5am.

Which leads me to a new construct!

**Programming construct \#3 - Booleans**

**A Boolean one of two states of being in the computer universe: “True”
or “False”**

Computers have no “maybe”.

In the example about the boy asking the girl out, the variables
“boyLike” and “girlLike” were really booleans. You just weren’t ready
for that information. Now you are!

boyLike = True

girlLike = True

girlAnswer = Null.

**WHAT, is NULL?!**

Null is nothing. literally. You for the most part can ignore null. You
won’t be using it much.

Remember I told you that the only two states of the universe were
**True** and **False**?

Well that is because if universe state is not **True** or **False**, it
must be **Null**

**Which is nothing.**

Null is actually a thing though, if you are curious, google it.

**Back to programming construct \#2 - Conditionals**

Conditionals are very intuitive to understand. That is because we use
conditionals in real life all the time.

**Conditionals evaluate the state of the universe based on a statement
that must be either “True” or “False” **

**There are three ways to write conditionals:**

1.  \#if a condition is met; do something:

**if universeState == True**

**do something**

1.  \#if a condition is met; do something; or else do something else:

**if universeState == True**

**do something**

**else** \#implies that universeSate must be false.

**do something else**

-   note - in the else bracket you don’t need to specify how to evaluate
    the universe. This is because the conditional is mutually exclusive
    and exhaustive. In this conditional either if the universe state is
    not true, it must be false.

1.  \#if a condition is met; do something; or else if another condition
    is met; do something different; or else (neither first two
    conditions are met); resort to catch-all action.

**if universeState ==True**

**do something**

**else if universeSate2 == True**

**do something different**

**else**

**resort to catch-all action.**

**Question: which programming construct has a secret built in
conditional??? **

In real life, and in programming, the state of the universe is
influenced by multiple factors. For example, to decide when to set my
alarm clock I need to not only evaluate what day of the week it is, but
also check that it is not a holliday.

I did this by **nesting** conditionals.

**if dayOfWeek != weekend**

**if holidayToday == False**

**only then set alarm clock to 5am**

**else**

**set alarm clock to 9:30am.**

Explanation: this is what the code did:

1.  checked if it was a weekend - if it was it went to the else clause
    and set alarm to 9:30;

2.  if it wasn’t a weekend it went down one conditional and checked if
    it was a holiday. if it was then it went to the else clause and set
    the alarm to 9:30.

3.  if it was not a holiday it set the alarm clock to 5am.

Essentially we had to check that it was a weekday, but not a holliday.

We had to check that it was a weekday **AND** not a holliday.

**Programming construct \#4 - Types**

You remember variables, they were construct \#***You must always name
them correctly***.

It turns out that variables are actually a little more tricky than they
would have you believe. As you remember, variables are units that store
“information”.

It turns out that information or **data** can be of several **types.**

**A type is a categorization of the data that determines the possible
values of that data; the operations that can be done on that type of
data; the meaning of the data; and the way values of that type can be
stored.**

Whoa!! long definition.

**How am I ever going to understand what a type is??? :(:(:(:(**

**It may cheer you up to know that you have just learned one type!**

**the BOOLEAN type :)**

The possible values of data of **Boolean type** are: **True/False.**

The operations that can be done on **Booleans** are: ‘==’, ‘!=’, ‘&&’
and ‘||’.

The meaning of the data is either **True or False**

The way that **Boolean type** is stored is in variables.

**There, that wasn’t so difficult, right?**

Types can be tricky, some languages make more of a fuss about usage of
the correct type than others. Bash (unix shell) is pretty relaxed about
types. Python is a quite a bit more fussy about types. Java is Extremely
fussy about types.

**What types of types exist?**

1.  **Char -** it just means a single character - as in ‘a’ or ‘7’,
    comes up in Matlab, Java etc.

2.  **String -** A string is a bunch of characters strung together. You
    can tell something is a *string* if it is surrounded by quotes.
    (“my string”).

    1.  the reason we need the quotes is that the quotes keep the string
        together, even if there are spaces, tabs or newlines in the
        middle of the string.

3.  **Int -** Short for “Integer”. An *int* is a number. with no
    decimal point.

4.  **Foat -** unlike an Int a **Float** has a decimal point. java
    refers to floats as “real” (real number).

**Ah, we have come to the source of fussy-ness in types.**

String myString = “123”

Int myInt = 123

if myString == myInt

echo “Yay!”

**PROBLEM: error: cannot compare incompatible types. \#crashBangUrp**

The reason you are not allowed to compare these types is that you are
comparing apples to oranges. myInt is a number. myString is a word. They
are not comparable.

**There is more to be said on the topic, google it.**

\***Note, there is also a “float” type. This is a number with a decimal
point. Guess what, you cannot compare an int with a float either. This
all boils down to the fact that the computer takes things very
literally. **

**Programming construct \#5 - “AND” & “OR” operators**

**An Operator in programming is like an Operator in Algebra.**

-   - % . ,|’ - are all operators.

**In programming:**

**&& means “and”**

**|| means “or”**

To demonstrate how these operators are used I will write a nicer version
of the conditional we wrote above:

**if (dayOfWeek == weekday) && (hollidayToday == False)**

**set my alarm to 5am.**

The way the computer evaluates this statements is the same as algebra:

first it evaluates the conditionals inside the parentheses and replaces
them with either true or false:

**An && statement requires both sides of the statement to be true.**

**An || statement requires only one of the statements to be true.**

**Note:**

**True == True \#is a true statement.**

**True == False \#is a false statement.**

**False == True \#is a false statement.**

**False == False \#is a true statement.**

**Constructs of more advanced programming:**

**(These are things you should google once you are a master of the first
constructs.)**

-   Functions.

-   Assigning variables to functions.

-   Arrays and lists and counters.

-   try/except.

-   break/continue.

-   mod operator.

**~ Bash Syntax ~**

## Below is the syntax for some bash supercommands, commonly executed in
the terminal. Please add your own: 

### Lists all files in current directory and when they were last edited

```
ll | awk '{ print $8 " Edited last on: " $7 " of " $6}'
```

### Prints to standard out all of the six digit directories in current directory

```
for i in \`ls | grep "\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]"\`;
do echo ${i}; done
```

### Does the same thing but also replaces all “0”s with “M”s

```
for i in \`ls | grep "\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]\[0-9\]"\`;
do echo ${i} | sed 's/0/M/g'; done
```


## Below is a list of commonly executed bash constructs 

### Loop through all the subjects in my project directory 
and extract get their subjectID

```
for i in /NAS_II/Projects/K_lab/MTBI/\[A-Z\]\[0-9\]\[0-9\]\[0-9\]
do
subjId=${i\#\*"MTBI/"}
if \[ \]
then
elif \[ \] 
then
else
echo ${subjID}
fi
done
```

### Reading a file line by line with a while loop

```
while read line
do
echo $line
done < file.t 
```

### How to use Arrays:

```
myArray=()
count=1
#fill the array:
for i in $my people
do
myArray[$count]=$i
count=\`expr $count + 1\`
done
```

### print out the array:

```
for i in ${myArray[@]}
do
echo $i
done
```

### How to use the && operator:

```
if [ ! "$oflag" -a ! "$tflag" ]
then
exit 1
fi
```

### How to define functions:

```
myFunction()
{
#do stuff
}
```

### Comparing ints or doing math:

```
while [ $noletter -le $length ]
do
array[$x]=$1
noletter=$(( noletter + 1 ))
x=$(( $x + 1 ))
done
```

### Comparing strings:

```
if [ $tval == "noaccess" ]
then
fi
```

### Getops:

```
Usage()
{
echo "Usage: $0: [-o <output prefix> ] {OPTIONAL: [-a <Nback1.nii.gz> ] [-b <Nback2.nii.gz> ]"
exit 2
}

#parse arguments & help:

aflag=
bflag=
oflag=
while getopts 'a:b:o:' OPTION
do
case $OPTION in
o) oflag=1
oval="$OPTARG"
;;

a) aflag=1
aval="$OPTARG"
;;

b) bflag=1
bval="$OPTARG"
;;

**?) printf "Usage: $0: [-o <output prefix> ] {OPTIONAL: [-a
<Nback1.nii.gz>] [-b <Nback2.nii.gz>]"
exit 2
;;

esac
done

if [ ! "$oflag" ]
then
  echo "Please enter a -o &lt;output prefix&gt; argument."
  Usage
  exit 1
fi
```

### How to view results of dual regression:

```
for i in *file*
do
 echo $i
 fslstats $i -R
done
```

### How to make results tables for all FEAT directories in a given directory 
(after making sure to shorten the FEAT directory names as much
as feasibly possible):

[STAGE 1]

```
for i in `ls -1`; do
/NAS_II/Projects/K_lab/SCRIPTS/Make_Feat_Result_Tables/mScript_Get_feat_stats
`echo ${i} | awk -F "/" '{ print $1 }'\`; done
```

[STAGE 2]
