---
layout: page
title: Some Basic Commands
---



Enough talk, let's get our hands dirty and start learning how to actually use Cowboy. If you're not logged in, log in and enter the following command:

	whoami

This command is fairly well named. It returns your user name. Let's move onto more interesting things. Input the following command:

	git clone git@github.com:OSU-HPCC/New-User-Tutorial.git

Don't worry about the details of this command yet. In short, this command downloads the files from this tutorial site into your user's home directory so that you can work with the examples that we have made for you. When you enter this command, you may get a message about adding unknown hosts. This is a security feature since you have never connected to our website from Cowboy before so it wants to make sure all is safe before connecting to a strange computer. Type `yes` and hit \<enter\>.

Listing Files
-------------

If all goes well you will see some text that looks something like this:

	remote: Counting objects: 31, done.
	remote: Compressing objects: 100% (29/29), done.
	remote: Total 31 (delta 9), reused 0 (delta 0), pack-reused 0
	Receiving objects: 100% (31/31), 11.51 KiB, done.
	Resolving deltas: 100% (9/9), done.

This means you have downloaded our files into your home directory. Lets take a look and see. Enter the following command:

	ls

You should at least see `New-User-Tutorial` listed on your screen and possibly even some other items as well. `ls` is short for list. This is how we see all the files in a directory. For example, when we double click on a folder in the Macintosh OS or in Windows, a window pops open with all the files and folders that are inside of that directory. It's the same idea on a Linux terminal. We start within a directory and we can list all the files and sub-directories inside of the directory by using the `ls` command. Which brings us to our second Linux command. We need to know what directory we are in. Unfortunately, the 'Where am I?' command is not as well named as the 'Who am I?' command:

	pwd

`pwd` stands for 'print working directory' and tells us what directory we are currently in. Hopefully your output looks something like:

	/home/monkey


File Systems and Changing Location
----------------------------------
In the example above, `pwd` gave us a list separated by the '/' character. Think back to our example from Windows or Macintosh OS. When we need to find a file on these systems we double click on the *Hard Drive* icon in Macintosh OS or the *C:* drive in Windows. We are then presented with a list of sub directories and files. We can continue double-clicking on sub directories to see what is inside of successive folders. For example, if I wanted to open iTunes on my Macintosh, I could double click *Hard Drive*, then double click *Applications*, and finally double click iTunes. If I were to describe where iTunes is located on my computer I could make a list of directories and sub directories separated by '/': `/Hard_Drive/Applications`. The same principle applies here. `/home/monkey` tells us our location on the computer by showing us what folders we must travel through to get to the directory `monkey`. The very 'first' file on the computer is represented by the first '/' (all the other '/' are simply used as separators in our list of folders). From here we can travel along all the different possible paths to get to any file on the computer. Since in each directory you can choose from many different sub directories, the path you take can branch out in many directions. We use the analogy of a tree and describe the first '/' as the root, and the whole system of files as the 'directory tree.'

So right now we are in the `/home/monkey` directory. As usual, your path will have your user name, not monkey. This directory is called your home directory. Every user gets a home directory when their account is setup on Cowboy. This directory has a quota of 25GB and you can use it to store your source code and executable programs. Please note that this directory is **NOT BACKED UP**, so please keep a backup of all your files on your personal computer. Each user on Cowboy is also given a folder in the `/scratch` directory. For user monkey, that directory is called `scratch/monkey`. This folder is for the user to store large files and large collections of files. Please note, this file system is also **NOT BACKED UP** so please keep a personal backup of your files.

Let's check out our scratch folder. Type the following commands:

	pwd
	cd /scratch/monkey
	pwd

You should get the following output:

	/home/monkey
	/scratch/monkey

`cd` stands for 'change directory'. It is the tool that allows us to move to a different folder. Notice, we started off in the /home/monkey directory and now we are in the /scratch/monkey directory. Do you have any files in this directory? Do you remember how to find out? Let's head back to our home directory. Type the following commands:

	cd
	pwd

Now we are back in the home directory but we didn't tell `cd` what file we wanted to go. If we don't give `cd` the directory that we want to go to, it will automatically take us to our home folder. So if you ever get lost, just enter `cd` to go home.

Looking Inside Files
--------------------
Are you in your home directory? If not, go ahead and head home by using `cd`. Let's take a look at the files that you downloaded earlier. Go ahead and move into the `New-User-Tutorial` directory. What files are in `New-User-Tutorial`? Using `ls` you should see something similar to this:

	copiedfiles  copiedfiles2  examplescripts  misc  README.md

We can see that there are three directories and one file called `README.md`. It's always a good idea to read the README first so lets have a look:

	cat README.md

The `cat` command takes the content of a text file and prints it out to your screen. We can see that if you are reading this tutorial you don't need to read the contents of `README.md`, but before we move on lets try the command one more time. This time don't type the full file name. Stop typing after `cat RE` and then hit the \<tab\> button on your keyboard. Did you notice that Cowboy filled in the rest of the command for us? Linux gives us a tab-complete feature. As soon as we have typed enough of the file name for the computer to distinguish it from the other files, hitting tab will automatically fill in the rest of the file name. In this case we could type in `cat R` and hit tab and it would complete the file name since no other files or directories start with 'R.' This saves us a lot of typing, especially if we are working with long file names. Tab completion also works on commands. Type the following and hit \<tab\> twice:

	ca

We get a list of all possible commands starting with 'ca' (what you see may be a slight variation of this list):

	cacertdir_rehash    canberra-gtk-play   captoinfo
	cal                 cancel              cas
	caller              cancel.cups         cas-admin
	callgrind_annotate  canceljob           case
	callgrind_control   capinfos            cat
	cameratopam         capsh               catchsegv

We will just focus on `cat` during this tutorial, but later we will see how we can explore unknown commands.

Copying and Moving Files
------------------------
Let's have a look at some of the directories in our folder:

	ls copiedfiles2

Noticed nothing happened. That's because `copiedfiles2` is empty so there are no files or sub directories to list. Lets try again with another directory:

	ls copiedfiles

We see that `copiedfiles` has ten text files:

	copynumber01.txt  copynumber04.txt  copynumber07.txt  copynumber10.txt
	copynumber02.txt  copynumber05.txt  copynumber08.txt
	copynumber03.txt  copynumber06.txt  copynumber09.txt

Now we're going to copy one of our files into the empty `copiedfiles2` directory:

	cp copiedfiles/copynumber05.txt copiedfiles2/
	ls copiedfiles2

`cp` is our command for copy. We always make the first argument for the command the file we want to copy in its location and the second argument is the place we want to copy it to. We've now made a copy of `copynumber05.txt` and put that copy into the `copiedfiles2` directory. Now lets move into `copiedfiles2` and make another copy:

	cd copiedfiles2
	cp copynumber05.txt copynumber05copy.txt 
	ls

If we `cat` the two files, we can see that they are identical copies. Notice this time since we are in the `copiedfiles2` directory we only use the name of the file and the name of the new file. `cp` assumes the whole operation will stay in `copiedfiles2`.

Now let's try to move a file. We are already in the `copiedfiles2` directory so we can use the move (`mv`) command as follows:

	mv ../copiedfiles/copynumber10.txt .
	ls

We have three new concepts happening with this command. First, we are using the new `mv` command which moves files instead of copying them. Second, we put `..` at the beginning of the first file path. This is a shortcut that saves us some typing. `..` tells the computer that you mean the 'parent directory,' or the next directory up. If we use the `pwd` command to see which directory we are in, the 'parent directory' is the second to the last directory in the list. Finally, `.` is shorthand for my current directory. So this command has moved `copynumber10.txt` into `copiedfiles2`. We see that `copiedfiles2` now has the following files:

	copynumber05copy.txt  copynumber05.txt  copynumber10.txt


Comparing Two Files
-------------------

We're in the `copiedfiles2` directory so lets try and compare the different files we have:

	diff copynumber05.txt copynumber10.txt

We see the following output:

	< I'm copy number: 5.
	---
	> I'm copy number: 10.

As you may have guessed, `diff` shows us the difference between two files. It outputs all the lines that are different between two files. In this case, the first file had only one line: 'I'm copy number: 5.' which happened to be different than the second file's only line: 'I'm copy number: 10.'. Try using `diff` to compare `copynumber05.txt` and `copynumber05copy.txt`. Notice we get no output because there is no difference between the two files.

Editing Files
-------------

We now know how to explore the directories and files on Cowboy, but how about changing files? Type the following commands:

	cd ../copiedfiles
	nano copynumber01.txt

`nano` is a text editor (similar to Word on your personal computer) that is terminal based. By typing nano and then the file name, we have opened `copynumber01.txt` inside the nano text editor. Now we can change `copynumber01.txt`. Let's do that. Go ahead and add the line `Go Cowboys!` below `I'm copy number: 1.` Now, notice at the bottom there are a list of commands that we can execute. The '^' is an abbreviation for the \<ctrl\> key on your keyboard. Let's exit by hitting \<ctrl-x\>. We're asked `Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES)?` because we didn't save our changes. Type `Y`. Now we are asked `File Name to Write:` Here we could change the name of our file (like 'Save As' in Word). The default is to keep the file name the same which we will do by hitting \<enter\>, and nano exits. Now if we `cat copynumber01.txt` we see that the contents of the file have been changed.

Searching Files for Patterns
----------------------------

So we have edited `copynumber01.txt` and let us invision a scenario where several weeks have passed and we have now forgetten which file we added the line 'Go Cowboys!' to. We need a way to search through the files and find the file we edited. We can do that with the following command:

	grep 'Go Cowboys!' *

`grep` tells us what file our search can be found in. `grep` takes what is known as a regular expression and looks for it in a file or a list of files. Regular expressions are beyond the scope of this tutorial, but if you are interested you can check out the `additionalresources` directory in `misc`, or click [here][additonalresources]. For now, just know that you can put the text you want to search for in quotes and `grep` will try to match it in the list of files that you specify. Notice however, that I did not give `grep` a list of files, but instead used a '\*' character. This is what is known as wild card. '\*' tells the computer to automatically fill in all possible files. In this case, the Cowboy fills in all the 'copynumber...' files where the '\*' was, which saves us lots of typing. Another important wild card is '?'. While '\*' will be filled in by the computer with any number of characters, '?' tells the computer to fill in this spot with all possibilities for one character only. For example, we could repeat the above search using '?' with the following command:

	grep 'Go Cowboys!' copynumber??.txt

Let's try another search:

	grep 'go cowboys!' copynumber??.txt

Notice this time we didn't get any results back. That's because `grep` is case sensitive. We can make `grep` ignore case by typing the following:

	grep -i 'go cowboys!' copynumber??.txt

Notice we get the first output again. `-i` is known as an option. All commands have options. It allows us to change something about the way the command works. To use an option, type the command then '-' followed by the option abbreviation, and then the arguments for the command (don't forget to separate everything by a space). In this case, `-i` tells `grep` to ignore case in its search.

Deleting Files
--------------

Let's try one more wild-card exercise:

	cat *

Remember that '\*' will be filled in with all possible files by the computer so cat outputs the content of all the files in `copiedfiles` at the same time:

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

We notice that 'Go Cowboys!' doesn't match the pattern so we decide to delete `copynumber01.txt`:

	rm copynumber01.txt

If we use the `ls` command, we can see that `copynumber01.txt` is no longer in the direcotry. `rm` stands for remove and you must always be sure when using it because it is permanent. There is no 'Recycle Bin' in Linux. Once your delete a file by using `rm`, it is permanent. There is no way to get it back. This is a good time to remind our users that user files are **not backed up** on Cowboy. So please make sure to keep a personal backup of all of your files.

Miscellaneous Commands
----------------------

Nice work, we've learned quite a few basic commands and you should feel comfortable moving around Cowboy. Next we will learn how to use the software packages on Cowboy and how to submit a job to the compute nodes, but before we get there, there are a few more commands that you might find helpful. First, try hitting the \<up-arrow\> on your keyboard. Notice that the last command you typed appears. In fact, you can keep hitting the \<up-arrow\> to go back through the list of commands you have used already. This is yet another feature that saves on typing since we often need to use the same command multiple times. Another command that might be helpful is `man`. `man` stands for manual, and almost every command in Linux has a manual entry. If you come across a new command or would like to know more about all the possible options for a command type `man` followed by the command name. Want to test yourself? try to use the following command and see if you can use the manual to find out what `ls -a` does:

	man ls

Once you find out all the new options for `ls` try them out. This is a great way to learn new commands. The only downside of `man` is that it can sometimes become a bit technical. If you find that the `man` page is not answering your questions, try googling the command with the word 'Linux'. Often the first link will be a page with a practical example of the command actually being used. Finally, if you enter a command and realized it was a mistake, you can always use \<ctrl-c\> to cancel whatever process the terminal is currently doing. Analogous to \<ctrl-alt-delete\> in Windows, \<ctrl-c\> is Linux's version of 'I'm just kidding, stop that!' It may take a moment or two for the system to respond so don't worry, you only need to use it once. That's all the basic commands we will cover in this tutorial. Next we will learn how to use the software that has been installed on the Cowboy system.

[Next]({{ site.url }}{{ site.baseurl }}/modules.html)

