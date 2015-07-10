---
layout: tutorial
title: Logging In
---

Windows
-------
- If you are logging into cowboy from a Windows machine, you will need to install a program called putty. You can download putty [here][putty].
- Once you have downloaded putty and started it, you should see a screen that looks something like this:

  ![Puttyimg]({{ site.url }}{{ site.baseurl }}/img/putty.JPG)


- In the box labeled *Host Name*, type **cowboy.hpc.okstate.edu**.
- Check to make sure that the *Connection Type* is **ssh** and the *Port* number is **22**.
- To save your session for next time (so you don't have to retype each time) type a name into *Saved Sessions* and click *Save*. Next time you log in, all you will need to do is double click on the saved session name.
- Click *Open* to open a connection with Cowboy. You will be asked for your password. **No characters will appear when you type in the password**. This is a security feature. Don't worry, just type the password you received when you set up your account and hit \<enter\>.
- You should now have a command prompt. To log out, simply type `exit` or `logout` and hit \<enter\>.

[putty]: http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe

Linux
-----
Launch a terminal, type the following and hit enter:

	ssh username@cowboy.hpc.okstate.edu

In the above example, 'username' is your user name. For example, if your user name was 'monkey,' you would type:

	ssh monkey@cowboy.hpc.okstate.edu


Macintosh
---------
Since the Macintosh OS is based off of Unix just like Linux, logging into Cowboy is very similar to logging in from a Linux computer:

-	Double click on the *Hard Drive* icon.
-	Double click on the *Applications* folder.
-	Double click on the *Utilities* folder.
-	Double click on *Terminal*.

Now that you have launched the terminal, follow the same directions as logging in with a Linux computer.


First Time on Cowboy
====================
Note: This tutorial is long, but there is some great information in it and we worked hard to make Cowboy as accessible as possible for new users. If you have some familiarity with Linux already you probably only need to skim the tutorial for Cowboy-specific information, but if you are new to Linux, you should take the time to work through the whole tutorial. We know life is busy so if you need to stop between sections, we have made it easy for you to do so. When you come back log into Cowboy and then hover your mouse over the next section in this tutorial. The command you need to get back where you left off will appear. Enter these commands into your Cowboy session and you will be ready to pick up where you left off.

Changing your Password
----------------------
The first time you log into Cowboy, you should change your password from the default password assigned when your account was created to a more secure (and easier to remember) password of your choosing. Type the following and hit enter:

	passwd

You should see the following text (for the purposes of this tutorial we will use the example user name monkey):

	Changing password for user monkey.
	Current Password:

Type in your current password (currently the default password assigned to you) and hit \<enter\>. You will then be prompted to enter a new password twice. From now on, you will log into Cowboy with this new password. Please note that Cowboy is accessible from any computer with an Internet connection so please choose a **STRONG** password.

Notes on Using the Terminal
------------------

###Login Nodes###

When you log into Cowboy, you are actually logged into one of Cowboy's two login nodes. Remember, Cowboy is actually a network of many computers ("nodes") linked together by a high speed network so that they can communicate and can combine computing power in order to complete a task faster than any single computer. Cowboy has 254 compute nodes and two login nodes. When you log in, you might see a prompt that looks something like this:

	[monkey@login2 ~ ]$

This means that you are currently logged into the second login node on Cowboy. These two nodes are for logging in, working with files, and for submitting jobs. Always submit jobs to the scheduler, and never run a job from a login node. We will explain job submission more thoroughly later in this tutorial.

###Using the Mouse###

When logged into Cowboy, you are using a terminal so you mouse does not do anything. All commands are typed and interaction with the computer is text based. The one exception is that your mouse can be used to copy and paste. If you highlight any text in the terminal with your mouse it is automatically copied. To paste it either right click (in putty) or click the middle button/scroll wheel of your mouse.

###Why Use a Terminal?###

So why use a terminal? Wouldn't it be easier if Cowboy had a graphical user interface (GUI) with buttons and a mouse like most modern personal computers? While there is a steep learning curve associated with using a terminal, terminal based computer systems are ideally suited for scientific computing. Consider a research scientist who has data files containing the results of their research. Each run of the experiment contains data from that run and in the course of their research, the scientist must make a change to each one of the files. If there are only twenty data files then clicking on each file to open it and change it, while time consuming is doable. However, what does the scientist do for an experiment that has 200 runs, or even 2,000? Unless they employ a lot of graduate students, our poor research scientist will not be able to complete their research in a timely manner. The terminal has a nice set of features that allows us to automate such tasks so that the computer does the work for us. We will talk more about these options later. Remember, while the terminal has a steep learning curve, it is an investment that pays itself back later by saving you time.

You're now ready to move on to [Basic Commands]({{ site.url }}{{ site.baseurl}}/somebasiccommands.html).
