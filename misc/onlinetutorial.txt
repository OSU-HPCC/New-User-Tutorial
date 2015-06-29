Logging Into Cowboy
===================
Windows
-------
- If you are logging into cowboy from a Windows machine, you will need to install a program called putty. You can download putty [here][putty].
- Once you have downloaded putty and started it, you should see a screen that looks something like this:
- In the box labeled *Host Name*, type **cowboy.hpc.okstate.edu**.
- Check to make sure that the *Connection Type* is **ssh** and the *Port* number is **22**.
- To save your session for next time (so you don't have to retype each time) type a name into *Saved Sessions* and click *Save*. Next time you log in, all you will need to do is double click on the saved session name.
- Click *Open* to open a connection with Cowboy. You will be asked for your password. **No characters will appear when you type in the password**. This is a security feature. Don't worry, just type the password you received when you set up your account and hit enter.
- You should now have a command prompt. To log out, simply type exit or logout and hit enter.

[putty]: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html

Linux
-----
Launch a terminal, type the following and hit enter:
```
ssh username@cowboy.hpc.okstate.edu
```
In the above example, 'username' is your user name. For example, if your user name was 'monkey,' you would type:
```
ssh monkey@cowboy.hpc.okstate.edu
```

Macintosh
---------
Since the Macintosh OS is based off of Unix just like Linux, logging into Cowboy is very similar to logging in from a Linux computer:
- Double click on the *Hard Drive* icon.
- Double click on the *Applications* folder.
- Double click on the *Utilities* folder.
- Double click on *Terminal*.
Now that you have launched the terminal, follow the same directions as logging in with a Linux computer.


First Time on Cowboy
====================
Note: This tutorial is long, but there is some great information in it and we worked hard to make Cowboy as accessible as possible for new users. If you have some familiarity with Linux already you probably only need to skim the tutorial for Cowboy-specific information, but if you are new to Linux, you should take the time to work through the whole tutorial. We know life is busy so if you need to stop between sections, we've made it easy for you to do so. When you come back log into Cowboy and then hover your mouse over the next section in this tutorial. The command you need to get back where you left off will appear. Enter these commands into your Cowboy session and you will be ready to pick up where you left off.

Changing your Password
----------------------
The first time you log into Cowboy, you should change your password from the default password assigned when your account was created to a more secure (and easier to remember) password of your choosing. Type the following and hit enter:
```
passwd
```
You should see the following text (for the purposes of this tutorial we will use the example user name monkey):
```
Changing password for user monkey.
Current Password:
```
Type in your current password (currently the default password assigned to you) and hit enter. You will then be prompted to enter a new password twice. From now on, you will log into Cowboy with this new password. Please note that Cowboy is accessible from any computer with an Internet connection so please choose a **STRONG** password.

Notes on Using the Terminal
------------------
###Login Nodes###
When you log into Cowboy, you are actually logged into one of Cowboy's two login nodes. Remember, Cowboy is actually a network of many computers ('nodes') linked together by a high speed network so that they can communicate and can combine computing power in order to complete a task faster than any single computer. Cowboy has 254 compute nodes and two login nodes. When you log in, you might see a prompt that looks something like this:
```
[monkey@login2 ~ ]$
```
This means that you are currently logged into the second login node on Cowboy. These two nodes are for logging in, working with files, and for submitting jobs. Always submit jobs to the scheduler, and never run a job from a login node. We will explain job submission more thoroughly later in this tutorial.
###Using the Mouse###
When logged into Cowboy, you are using a terminal so you mouse does not do anything. All commands are typed and interaction with the computer is text based. The one exception is that your mouse can be used to copy and paste. If you highlight any text in the terminal with your mouse it is automatically copied. To paste it either right click (in putty) or click the middle button/scroll wheel of your mouse.
###Why Use a Terminal?###
So why use a terminal? Wouldn't it be easier if Cowboy had a graphical user interface (GUI) with buttons and a mouse like most modern personal computers? While there is a steep learning curve associated with using a terminal, terminal based computer systems are ideally suited for scientific computing. Consider a research scientist who has data files containing the results of their research. Each run of the experiment contains data from that run and in the course of their research, the scientist must make a change to each one of the files. If there are only twenty data files then clicking on each file to open it and change it, while time consuming is doable. However, what does the scientist do for an experiment that has 200 runs, or even 2,000? Unless they employ a lot of graduate students, our poor research scientist will not be able to complete their research. The terminal has a nice set of features that allows us to automate such tasks so that the computer does the work for us. We will talk more about these options later. Remember, while the terminal has a steep learning curve, it is an investment that pays itself back later by saving you time.


Some Basic Commands
===================
Enough talk, let's get our hands dirty and start learning how to actually use Cowboy. If you're not logged in, log in and enter the following command:
```
whoami
```
This command is fairly well named. It returns your user name. Let's move onto more interesting things. Input the following command:
```
git clone git@github.com:OSU-HPCC/New-User-Tutorial.git
```
Don't worry about the details of this command yet. In short, this command downloads the files from this tutorial site into your user's home directory so that you can work with the examples that we have made for you. When you enter this command, you may get a message about adding unknown hosts. This is a security feature since you have never connected to our website from Cowboy before so it wants to make sure all is safe before connecting to a strange computer. Type yes and hit enter.

Listing Files
-------------
If all goes well you will see some text that looks something like this:
```
remote: Counting objects: 31, done.
remote: Compressing objects: 100% (29/29), done.
remote: Total 31 (delta 9), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (31/31), 11.51 KiB, done.
Resolving deltas: 100% (9/9), done.
```
This means you have downloaded our files into your home directory. Lets take a look and see. Enter the following command:
```
ls
```
You should see at least 'New-User-Tutorial' listed on your screen and possibly even some other items as well. `ls` is short for list. This is how we see all the files in a directory. For example, when we double click on a folder in the Macintosh OS or in Windows, a window pops open with all the files and folders that are inside of that directory. It's the same idea on a Linux terminal. We start within a directory and we can list all the files and sub-directories inside of the directory by using the `ls` command. Which brings us to our second Linux command. We need to know what directory we are in. Unfortunately, the 'Where am I?' command is not as well named as the 'Who am I?' command:
```
pwd
```
`pwd` stands for 'print working directory' and tells us what directory we are currently 'in.' Hopefully your output looks something like:
```
/home/monkey
```

File Systems and Changing Location
----------------------------------
In the example above, `pwd` gave us a list separated by the '/' character. Think back to our example from Windows or Macintosh OS. When we need to find a file on these systems we double click on the *Hard Drive* icon in Macintosh OS or the *C:* drive in Windows. We are then presented with a list of sub directories and files. We can continue double-clicking on sub directories to see what is inside of successive folders. For example, if I wanted to open iTunes on my Macintosh, I could double click *Hard Drive*, then double click *Applications*, and finally double click iTunes. If I were to describe where iTunes is located on my computer I could make a list of directories and sub directories separated by '/': `/Hard_Drive/Applications`. The same principle applies here. `/home/monkey` tells us our location on the computer by showing us what folders we must travel through to get to the directory `monkey`. The very 'first' file on the computer is represented by the first '/' (all the other '/' are simply used as separators in our list of folders). From here we can travel along all the different possible paths to get to any file on the computer. Since in each directory you can choose from many different sub directories, the path you take can branch out in many directions. We use the analogy of a tree and describe the first '/' as the root, and the whole system of files as the 'directory tree.'

So right now we are in the `/home/monkey` directory. As usual, your path will have your user name, not monkey. This directory is called your home directory. Every user gets a home directory when their account is setup on Cowboy. This directory has a quota of 25GB and you can use it to store your source code and executable programs. Please note that this directory is **NOT BACKED UP**, so please keep a backup of all your files on your personal computer. Each user on Cowboy is also given a folder in the `/scratch` directory. For user monkey, that directory is called `scratch/monkey`. This folder is for the user to store large files and large collections of files. Please note, this file system is also **NOT BACKED UP** so please keep a personal backup of your files.

Lets check out our scratch folder. Type the following commands:
```
pwd
cd /scratch/monkey
pwd
```
You should get the following output:
```
/home/monkey
/scratch/monkey
```
`cd` stands for 'change directory'. It is the tool that allows us to a different folder. Notice, we started off in the /home/monkey directory and now we are in the /scratch/monkey directory. Do you have any files in this directory? Do you remember how to find out? Let's head back to our home directory. Type the following commands:
```
cd
pwd
```
Notice, we are back in the home directory but we didn't tell `cd` what file we wanted to go. If we don't give `cd` the directory that we want to go to, it will automatically take us to our home folder. So if you ever get lost, just enter `cd` to go home.

Looking Inside Files
--------------------
Are you in your home directory? If not, go ahead and head home by using `cd`. Let's take a look at the files that you downloaded earlier. Go ahead and move into the `New-User-Tutorial` directory. What files are in `New-User-Tutorial`? Using `ls` you should see something similar to this:
```
copiedfiles  copiedfiles2  examplescripts  misc  README.md
```
We can see that there are three directories and one file called `README.md`. It's always a good idea to read the README first so lets have a look:
```
cat README.md
```
The `cat` command takes the content of a text file and prints it out to your screen. We can see that if you are reading this tutorial you don't need to read the contents of `README.md`, but before we move on lets try the command one more time. This time don't type the full file name. Stop typing after `cat RE` and then hit the `tab` button on your keyboard. Notice Cowboy filled in the rest of the command for us. Linux gives us a tab-complete feature. As soon as we have typed enough of the file name for the computer to distinguish it from the other files, hitting tab will automatically fill in the rest of the file name. In this case we could type in `cat R` and hit tab and it would complete the file name since so other files or directories start with 'R.' This saves us a lot of typing, especially if we are working with long file names. Tab completion also works on commands. Type the following and hit tab twice:
```
ca
```
We get a list of all possible command starting with 'ca' (what you see may be a slight variation of this list):
```
cacertdir_rehash    canberra-gtk-play   captoinfo
cal                 cancel              cas
caller              cancel.cups         cas-admin
callgrind_annotate  canceljob           case
callgrind_control   capinfos            cat
cameratopam         capsh               catchsegv
```
We will just focus on `cat` during this tutorial. Later we will see how we can explore unknown commands.

Copying and Moving Files
------------------------
Let's have a look at some of the directories in our folder:
```
ls copiedfiles2
```
Noticed nothing happened. That's because `copiedfiles2` is empty so there are no files or sub directories to list. Lets try again with another directory:
```
ls copiedfiles
```
We see that `copiedfiles` has ten text files:
```
copynumber01.txt  copynumber04.txt  copynumber07.txt  copynumber10.txt
copynumber02.txt  copynumber05.txt  copynumber08.txt
copynumber03.txt  copynumber06.txt  copynumber09.txt
```
Now we're going to copy one of our files into the empty `copiedfiles2` directory:
```
cp copiedfiles/copynumber05.txt copiedfiles2/
ls copiedfiles2
```
`cp` is our command for copy. We've now made a copy of `copynumber05.txt` and put that copy into the `copiedfiles2` directory. Now lets move into `copiedfiles2` and make another copy:
```
cd copiedfiles2
cp copynumber05.txt copynumber05copy.txt 
ls
```
If we `cat` the two files, we can see that they are identical copies. Notice this time since we are in the `copiedfiles2` directory we only use the name of the file and the name of the new file. `cp` assumes the whole operation will stay in `copiedfiles2`.

Now let's try to move a file. We are already in the `copiedfiles2` directory so we can use the move (`mv') command as follows:
```
mv ../copiedfiles/copynumber10.txt .
ls
```
We have three new concepts happening with this command. First, we are using the new `mv` command which moves files instead of copying them. Second, we put `..` at the beginning of the first file path. This is a shortcut that saves us some typing. `..` tells the computer that you mean the 'parent directory,' or the next directory up. If we use the `pwd` command to see which directory we are in, the 'parent directory' is the second to the last directory in the list. Finally, `.` is shorthand for my current directory. So this command has moved `copynumber10.txt` into `copiedfiles2`. We see that `copiedfiles2` now has the following files:
```
copynumber05copy.txt  copynumber05.txt  copynumber10.txt
```

Comparing Two Files
-------------------
We're in the `copiedfiles2` directory so lets try and compare the different files we have:
```
diff copynumber05.txt copynumber10.txt
```
We see the following output:
```
< I'm copy number: 5.
---
> I'm copy number: 10.
```
As you may have guessed, `diff` shows us the difference between two files. It outputs all the lines that are different between two files. In this case, the first file had only one line: 'I'm copy number: 5.' which happened to be different than the second file's only line: 'I'm copy number: 10.'. Try using `diff` to compare `copynumber05.txt` and `copynumber05copy.txt`. Notice we get no output because there is no difference between the two files.

Editing Files
-------------
So now we know how to explore the directories and files on Cowboy, but how about changing files? Type the following commands:
```
cd ../copiedfiles
nano copynumber01.txt
```
`nano` is a text editor (similar to Word on your personal computer) that is terminal based. By typing nano and then the file name, we have opened copynumber01.txt inside the nano text editor. Now we can change copynumber01.txt. Let's do that. Go ahead and add the line `Go Cowboys!` after `I'm copy number: 1.`. Now notice at the bottom there are a list of commands that we can execute. The '^' is an abbreviation for the CTRL key on your keyboard. Let's exit by hitting CTRL-x. We're asked `Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES)?` because we didn't save our changes. Type `Y`. Now we are asked `File Name to Write:`. Here we could change the name of our file (like 'Save As' in Word). The default is to keep the file name the same which we will do by hitting ENTER, and nano exits. Now if we `cat copynumber01.txt` we see that the contents of the file have been changed.

Searching Files for Patterns
----------------------------
So we have edited `copynumber01.txt` and lets say that several weeks have passed and we have now forgetten which file we added 'Go Cowboys!' We need a way to search through the files and find the file we edited. We can do that with the following command:
```
grep 'Go Cowboys!' *
copynumber01.txt:Go Cowboys!
```
Notice, `grep` tells us what file our search can be found int. `grep` takes what is known as a regular expression and looks for it in a file or a list of files. Regular expressions are beyond the scope of this tutorial, but if you are interested you can check out the `additionalresources` directory in `misc`. For now, just know that you can put the text you want to search for in quotes and `grep` will try to match it in the list of files that you specify. Notice however, that I did not give `grep` a list of files, but instead used a '*' character. This is what is known as wild card. '*' tells the computer to automatically fill in all possible files here. In this case, the Cowboy fills in all the 'copynumber...' files where the '*' was, which saves us lots of typing. Another important wild card is '?'. While '*' can will be filled in by the computer with any number of characters, '?' tells the computer to fill in this spot with all possibilities for one character only. For example, we could repeat the above search using '?' with the following command:
```
grep 'Go Cowboys!' copynumber??.txt
```
Let's try another search:
```
grep 'go cowboys!' copynumber??.txt
```
Notice this time we didn't get any results back. That's because `grep` is case sensitive. We can make `grep` ignore case by typing the following:
```
grep -i 'go cowboys!' copynumber??.txt
```
Notice we get the first output again. `-i` is known as an option. All commands have options. It allows us to change something about the way the command works. To use an option type the command then '-' followed by the option abbreviation, and then the arguments for the command (don't forget to separate everything by a space). In this case, `-i` tells `grep` to ignore case in its search.

Deleting Files
--------------
Let's try one more wild-card exercise:
```
cat *
```
Remember that '*' will be filled in with all possible files by the computer so cat outputs the content of all the files in `copiedfiles` at the same time:
```
I'm copy number: 1.
Go Cowboys!
I'm copy number: 2.
I'm copy number: 3.
I'm copy number: 4.
I'm copy number: 5.
I'm copy number: 6.
I'm copy number: 7.
I'm copy number: 8.
I'm copy number: 9.
I'm copy number: 10.
```
We notice that 'Go Cowboys!' doesn't match the pattern so we decide to delete `copynumber01.txt`:
```
rm copynumber01.txt
```
If we use the `ls` command, we can see that `copynumber01.txt` is no longer in the direcotry. `rm` stands for remove and you must always be sure when using it because it is permanent. There is no 'Recycle Bin' in Linux. Once your delete a file by using rm, it is permanent. There is no way to get it back. This is a good time to remind our users that user files are **not backed up** on Cowboy. So please make sure to keep a personal backup of all of your files.

Miscellaneous Commands
----------------------
Nice work, we've learned quite a few basic commands and you should feel comfortable moving around Cowboy. Next we will learn how to use the software packages on Cowboy and how to submit a job to the compute nodes, but before we get there, there are a few more commands that you might find helpful. First, try hitting the up-arrow on your keyboard. Notice that the last command you typed appears. In fact, you can keep hitting the up arrow to go back through the list of commands you have used already. This is yet another feature that saves on typing since we often need to use the same command multiple times. Another command that might be helpful is `man`. `man` stands for manual, and almost every command in Linux has a manual entry. If you come across a new command or would like to know more about all the possible options for a command type `man` followed by the command name. Want to test yourself? try to use the following command and see if you can use the manual to find out what `ls -a` does:
```
man ls
```
Once you find out all the new options for `ls` try them out. This is a great way to learn new commands. The only downside of `man` is that it can sometimes become a bit technical. If you find that the `man` page is not answering your questions, try googling the command with the word 'Linux'. Often the first link will be a page with a practical example of the command actually being used. Finally, if you enter a command and realized it was a mistake, you can always use ctrl-c to cancel whatever command. Analogous to ctrl-alt-delete in Windows, ctrl-c is Linux's version of 'I'm just kidding, stop that!' It may take a moment or two for the system to respond so don't worry, you only need to use it once. That's it, next we'll learn how to use the software that has been installed on the cowboy system.

Modules
=======

Available Software
------------------
We now know how to use Cowboy, but what good is using a supercomputer if we cannot use the software on it? Windows has the Start Menu and Macintosh OS has the launch bar, but how do we find out what programs or software are available on Cowboy when all we have is the command prompt? The answer is modules. Modules are an extremely powerful system that allows multiple users with different versions of software all to use the same machine at the same time, and it's how we will be using the software on Cowboy. First, it would be nice to know what software Cowboy has available for us to use:
```
module avail
```
We get output looking something like this:
```
---------------------------- /opt/modulefiles/Compilers -----------------------------
   cmake/3.0.0               mpich2/intel                  (D)
   cmake/3.1.3               mvapich/gnu
   cmake/3.2.2       (D)     mvapich/gnu-4.6.2
   cuda/toolkit-4.2          mvapich/intel                 (D)
   cuda/toolkit-5.5  (D)     mvapich2-1.8/gnu
   gcc-4.6.2                 mvapich2-1.8/gnu-4.6.2
   gcc-4.7.2                 mvapich2-1.8/intel            (D)
   gcc-4.8.4                 openmpi-1.4/gnu
   gcc-4.9.2                 openmpi-1.4/gnu-4.6.2
   intelmpi/4.1.0            openmpi-1.4/intel             (D)
   intelmpi/5.0.2    (D)     openmpi-1.6/gnu
   mpich2/gnu                test-dont-use/devtoolset-1.1
   mpich2/gnu-4.6.2

--------------------------- /opt/modulefiles/Applications ---------------------------
   R/2.15.1                               last/320
   R/2.15.2                       (D)     lastz/1.02
   R/3.0.2                                lastz/1.03.02
   R/3.1.2                                lastz/1.03.54                      (D)
   R/3.1.3                                libint/2.0.3
   R/3.2.1                                libxc/2.0.2-openmpi-intel
   abinit/6.12.3-openmpi-gnu              libxc/2.0.2
   abinit/7.0.4-openmpi-intel     (D)     libxc/2.2.1                        (D)
   abyss/1.3.7-openmpi-intel              log4cpp/1.1.1
   activeperl/5.18.1.1800                 lynx/2.8.7
   alignreads/2.4.0                       macaulay2/2.1.6
   alignreads/2.5.2-b-3           (D)     makedepend/1.0.5
   alignreads/2.23                        maker/2.28-openmpi-intel
   allpaths-lg/45553                      maker/2.28                         (D)
   amber/amber12                          mathematica/9.0.1
   amber/amber14                  (D)     mathematica/10.0.0                 (D)
   amos/3.0.0                             matio/1.5.2
   anaconda/1.6.1                 (D)     matlab/R2012b
   anaconda/2.2.0                         matlab/R2014a                      (D)
   ansys/15                               mauve/20120607
   antismash/2.0.2                        megacc/7.00-beta
   arb/5.5                                megan/megan5
   armadillo/4.300.8                      metapathways/1.0
   armadillo/4.550.2              (D)     metasim/0.9.5
   augustus/2.6.1                         mgltools/1.5.6
   augustus/3.0.1                 (D)     mgltools/1.5.7rc1                  (D)
   autoconf/2.69                          migrate-n/3.4.4-gcc
   autodock-vina/1.1.2                    migrate-n/3.4.4-openmpi-1.4-intel  (D)
   automake/1.15                          mira/3.4.1.1
--More--
```
Here we have a table listing all the software installed on Cowboy. Notice there are two general categories: Compilers, and Applications. Compilers are used by users who are writing their own code, while Applications work the exact same way as Applications in Windows or on a Macintosh (except no GUI). Look through the list and see if you can find `mathematica.` There are two entries: `mathematica/9.0.1` and `mathematica/10.0.0`. That's because there are two different versions of Mathematica installed on Cowboy and users are able to use either one. Next notice that some of the modules have a `(D)` next to them. Since there are multiple versions of each piece of software, certain versions are designated as default. In the case of Mathematica, if the user tells the computer to load Mathematica, but doesn't tell it which version to load, it will automatically load version 10.0.0. Finally, notice the word `--More--` at the bottom of the screen. The computer is telling us that the list keeps going. We can scroll down the list by hitting either enter (to go one line down) or space (to go one page down). Go ahead and scroll through until you get to the bottom of the list (your prompt will come back once the list has finished).

Spider
------
Once we reach the bottom of the list, we see that the module system has given us this helpful message:
```
Use "module spider" to find all possible modules. 
Use "module keyword key1 key2 ..." to search for all possible modules matching any 
of the "keys". 
```
The message is letting us know about a tool that is similar to `module avail`, but has many more features than just listing installed software. Let's give it a try:
```
module spider
```
Notice now we get the list of installed software, but this time each piece of software has a brief description that tells us what each piece of software is. Instead of scrolling to the bottom of the list type `q` to exit the list. This time try:
```
module spider mrbayes
```
We are given a brief description of a piece of software called MrBayes. We can see that there are several versions and if we want more detailed information about one of the specific versions, then we will need to do a search for that specific version. Lets do that (remember up arrow and then modify the command if you want to save typing):
```
module spider mrbayes/3.2.2-openmpi-intel
```
Now we are presented with a detailed description and help specific to that particular version of MrBayes. This is especially useful if we want to see whether or not the latest version of MrBayes has been installed on Cowboy. If you don't see the version of software that you need for your research and are an advanced user feel free to install the software in your home directory. Otherwise, you can contact and we will be more than happy to install it for you. You can also see a current list of the software in installed on Cowboy here.

Using Software
--------------
In order to use the software on Cowboy I need to 'load' the software module. We can see what software we have loaded by using the following command:
```
module list
```
We get an error message because we haven't loaded any software yet. Let's try Mathematica:
```
module load mathematica
```
Now when we use module list we get the following:
```
1) mathematica/10.0.0
```
which tells us that we are ready to use Mathematica. As a reminder, please remember that we are still in the login node and jobs should never be run from here. Instead submit the job to the scheduler which we will explain in the next section. Now let's get rid of Mathematica and instead load MrBayes:
```
module rm mathematica
module load mrbayes
```
Now when we use `module list` we see the following:
```
1) mrbayes/3.2.2-openmpi-intel    2) openmpi-1.4/intel    3) beagle/1.0
```
Wait a minute, why are there so many modules? Didn't we just load MrBayes? The beauty of modules is that it automatically loads mrbayes and any other software that mrbayes depends on to run. Now, if I want to go back to Mathematica there is actually a shortcut that I can use instead of using `module rm` and then `module load`:
```
module swap mrbayes mathematica
```
Let's reload MrBayes:
```
module load mrbayes
```
Now we have both Mathematica and MrBayes loaded. Feel free to use `module list` and check it out. Let's say we are done and we want to get rid of all of our modules. We can use the following command to unload all of our modules:
```
module purge
```

Batch Scheduler and Submit Scripts
==================================

Bash Scripts
------------
So far we have entered one command at a time, but we can actually give the computer many commands all at once by using scripts. The basic idea behind a script is that we can type several commands and save them as a text file. Later, we tell the computer to execute the file and it executes all the commands inside the file. This is especially helpful if we need to have the computer do a simple task for a large number of repetitions. Let's look at an example script(`~/` is an abbreviation that tells the computer to fill this symbol with the path to my home directory):
```
cd ~/New-User-Tutorial/misc
cat bashscriptexample.sh
```
Don't worry too much about all the details, we will just highlight one or two things. First, notice the first line of the file:
```
#!/bin/bash
```
This line is known as a shebang and tells the computer to execute our script with the `bash` program (the program we have been using to enter commands). The rest of the script is a loop:
```
for i in `seq 1 10`;
do
  echo "Look I can count: " $i
done
```
It tells the computer to output a message to the screen 10 times. Let's give it a try:
```
bash bashscriptexample.sh
```

Submit Scripts
--------------
In the name of education we have actually committed a supercomputer faux pas (in this case it was a faux pas because the task only repeated ten times, larger jobs may illicit emails from support staff). We ran a script from a login node. Remember: **ALL JOBS AND SCRIPTS SHOULD BE RUN THROUGH THE SCHEDULER.** Cowboy is a shared resource with many users all competing for compute time and the only fair way to split compute time between different users is to use the scheduler. The scheduler is also how our jobs gain access to Cowboy's compute nodes. Cowboy's scheduler is called `qsub`. We give our job to `qsub` by writing a bash script that tells qsub where to find our job and how to execute it and then `qsub` decides who and when our job should run in a way that is fair to all the users. Lets have a look at an example submit script:
```
cat examplesubmitscript.sub
```
As we can see, a submit script is basically a bash script, but there are a few extra lines that have been added for `qsub`. First, note that `#` is a comment marker in bash scripts. Anything typed after the `#` character is ignored by the computer. That is so humans can write notes in their files. This bash script is a little bit special. Since it is for `qsub` there are a few comment lines that are followed by `PBS`. These are special commands just for `qsub`, not for bash. Let's look at them:
```
#PBS -l nodes=1:ppn=1,walltime=5000
```
This tells `qsub` how many compute nodes we want to request for our job and how many processors we want from each node. In this case `nodes=1` asks the scheduler for 1 compute node and `ppn=1` requests 1 processor from the compute node. `walltime` tells the computer the time limit at which it should kill the program.
```
#PBS -q
```
This tells `qsub` which queue to put your job in. Cowboy has four queues:

- batch: The 'batch' queue is the default queue. The wall time limit is 120 hours (120:00:00). If your job needs to run longer than this and your software does not have checkpoint/restart capabilities, please email hpcc<at>okstate.edu for assistance as far in advance of your need as possible.

- express: The 'express' queue is for short jobs and debugging/testing scripts. The express queue contains 2 compute nodes and has a wall time limit of one hour (1:00:00).

- bigmem: The 'bigmem'queue directs jobs to one of the two compute nodes that have 256 GB RAM and a NVIDIA Tesla C2075 GPU card. The wall time limit is 120 hours (120:00:00).

- killable: The 'killable' queue is for long running jobs that are unable to use a checkpoint/restart feature. The wall time limit is 504 hours (504:00:00). Jobs in this queue are subject to being killed, at the discretion of HPCC administrators, for hardware and software issues.
```
#PBS -o myfirstjob.out
```
This tells `qsub` to put the output from your job in a text file called `myfirstjob.out`. Since you wont be able to see the result on your screen like when you execute commands in the login terminal, `qsub` will put everything that would have been printed to your screen into a text file for you to look at after the job has finished. This means you can go do something productive while Cowboy runs your job.
```
#PBS -j oe
```
By default Linux separates normal output and error. This puts them together and makes sure that if anything goes wrong with your job you will have all the error messages saved in your output file.
```
#PBS -m abe -M youremail@okstate.edu
```
This is the email feature. Once you submit your job to the scheduler this line tells Cowboy to send you an email when your job has finished. Which means you can log out and go do other things while Cowboy does its work.
```
cd $PBS_O_WORKDIR/
```
This line tells `qsub` to move into the directory that you submitted your script from. Now whatever commands happen after this point, it will be as if you submitted those commands to Cowboy from that directory. We can see that in this script we are loading the Mathematica module. Often people will create a master submit script and modify it for each specific job instead of writing a new one for each new job. Feel free to use this one as a template if you would like.

Submitting a Job
----------------
Enough talk, let's submit our job and see what happens. Open up the submit script with `nano` and change it so that it contains your email. Save and quit and then use the following command to submit the script:
```
qsub examplesubmitscript.sub
```
It will give a number. This is your job number and it allows you to track your job with the scheduler. Let's see how the job is doing:
```
showq -u monkey
```
Shows all of your jobs that are on the queue. We can also see all the other jobs on the queue by leaving off the user name option:
```
showq
```
Another command which is similar, but gives us just a little less information is:
```
qstat -u monkey
```
Finally, if we want to cancel our job, we use:
```
qdel 123456
```
This would remove my job from the queue if my job number was 123456.

Checking on Results
-------------------
Alright, did you get an email from Cowboy? Remember that we told Cowboy to put the output from the program into a file named `myfirstjob.out`? Simply move to the directory where you submitted the script from and have a look at `myfirstjob.out` to see what happened while your program was running on the compute nodes.


Additional Resources:
=====================
Congratulations, you finished the tutorial. Please have a look at `misc/additionalresources` if you would like more information on Linux, supercomputing, Cowboy, and many of the other topics that were covered in this tutorial. We have also included a cheat sheet of all the commands that were discussed in this tutorial: `misc/cheatsheet`. We hope you enjoy Cowboy. If you have any questions feel free to contact us.


Contact Information:
====================
**Dana Brunson, Ph.D.**
Director
High Performance Computing Center
MSCS 106
Oklahoma State University
Stillwater, OK 74078
Office: (405) 744-4455
dana.brunson<at>okstate.edu

**Jesse Schafer**
Manager of Operations
High Performance Computing Center
MSCS 105
Oklahoma State University
Office: (405) 744-4435
jessejs<at>okstate.edu

**Evan Linde**
Evan Linde
Research Cyberinfrastructure Analyst
High Performance Computing Center
MSCS 107a
Oklahoma State University
Office: (405) 744-1455
elinde<at>okstate.edu

**Angela K. Naff**
Angela K. Naff
Program Coordinator
High Performance Computing Center
MSCS 107
Oklahoma State University
Office: (405) 744-1914
angela.naff<at>okstate.edu

For user-support or general information about OSU-HPCC, please contact the team:
hpcc<at>okstate.edu
