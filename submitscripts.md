---
layout: tutorial
title: Submit Scripts
---



Bash Scripts
------------

So far we have entered one command at a time, but we can actually give the computer many commands all at once by using scripts. The basic idea behind a script is that we can type several commands and save them as a text file. Later, we tell the computer to execute the file and it executes all the commands inside the file. This is especially helpful if we need to have the computer do a simple task for a large number of repetitions. Let's look at an example script ( `~/` is an abbreviation that tells the computer to fill this symbol with the path to my home directory):

	cd ~/New-User-Tutorial/misc
	cat bashscriptexample.sh

Don't worry too much about all the details, we will just highlight one or two things. First, notice the first line of the file:

	#!/bin/bash

This line is known as a shebang and tells the computer to execute our script with the `bash` program (the program we have been using to enter commands). The rest of the script is a loop:

	for i in `seq 1 10`;
	do
	  echo "Look I can count: " $i
	done

It tells the computer to output a message to the screen 10 times. Let's give it a try:

	bash bashscriptexample.sh

As you become a more advanced user you will find that you create more and more of your own custom scripts.

Submit Scripts
--------------

In the name of education we have actually committed a supercomputer faux pas (in this case it was a faux pas because the task only repeated ten times, larger jobs may illicit emails from support staff). We ran a script from a login node. Remember: **ALL JOBS AND SCRIPTS SHOULD BE RUN THROUGH THE SCHEDULER.** If we run our jobs on a login node it will slow down and other users will not be able to log into Cowboy. Cowboy is a shared resource with many users all competing for compute time and the only fair way to split compute time between different users is to use the scheduler. The scheduler is also how our jobs gain access to Cowboy's compute nodes. Cowboy's scheduler is called `qsub`. We give our job to `qsub` by writing a bash script that tells qsub where to find our job and how to execute it and then `qsub` decides when and where our job should run in a way that is fair to all the users. Let's have a look at an example submit script:

	cat examplesubmitscript.sub

Your output should look like this:

	#!/bin/bash
	
	#These are PBS command
	
	#PBS -q express
	#PBS -l nodes=1:ppn=1,walltime=0:30:00
	#PBS -j oe
	#PBS -m abe -M youremail@okstate.edu
	
	cd $PBS_O_WORKDIR/  #This tells qsub to move 
	                    #to the directory that you 
	                    #submitted the script from.
	
	
	#Commands for your job go here:
	
	module load mathematica
	echo "Hello, I have loaded the Mathematica module, see:"
	module list
	echo "OK, my work here is done. Bye."


As we can see, a submit script is basically a bash script, but there are a few extra lines that have been added for `qsub`. First, note that '#' is a comment marker in bash scripts. Anything typed after the '#' character is ignored by the computer. That is so humans can write notes in their files. This bash script is a little bit special. Since it is for `qsub` there are a few comment lines that are followed by `PBS`. These are special commands just for `qsub`, not for bash. Let's look at them:

	#PBS -l nodes=1:ppn=1,walltime=0:30:00

This tells `qsub` how many compute nodes we want to request for our job and how many processors we want from each node. In this case `nodes=1` asks the scheduler for 1 compute node and `ppn=1` requests 1 processor from the compute node. `walltime` tells the computer the time limit at which it should kill the program. In this case, `0:30:00` refers to 30 minutes.

	#PBS -q express

This tells `qsub` which queue to put your job in. Cowboy has four queues:

-	batch: The 'batch' queue is the default queue. The wall time limit is 120 hours (120:00:00). If your job needs to run longer than this and your software does not have checkpoint/restart capabilities, please email us for assistance as far in advance of your need as possible.

-	express: The 'express' queue is for short jobs and debugging/testing scripts. The express queue contains 2 compute nodes and has a wall time limit of one hour (1:00:00).

-	bigmem: The 'bigmem'queue directs jobs to one of the two compute nodes that have 256 GB RAM and a NVIDIA Tesla C2075 GPU card. The wall time limit is 120 hours (120:00:00).

-	killable: The 'killable' queue is for long running jobs that are unable to use a checkpoint/restart feature. The wall time limit is 504 hours (504:00:00). Jobs in this queue are subject to being killed, at the discretion of HPCC administrators, for hardware and software issues.

You may also want to include a line that looks something like this even though we have not included it in this tutorial:

	#PBS -o myfirstjob.out

This tells `qsub` to put the output from your job in a text file called `myfirstjob.out`. Since you wont be able to see the result on your screen like when you execute commands in the login terminal, `qsub` will put everything that would have been printed to your screen into a text file for you to look at after the job has finished. This means you can go do something productive while Cowboy runs your job. If you don't give `qsub` an output file name it will automatically put it in a file named according to the job number. For this tutorial, we want `qsub` to do the default behavior.

	#PBS -j oe

By default Linux separates normal output and error. This puts them together and makes sure that if anything goes wrong with your job you will have all the error messages saved in your output file.

	#PBS -m abe -M youremail@okstate.edu

This is the email feature. Once you submit your job to the scheduler this line tells Cowboy to send you an email when your job has finished. Which means you can log out and go do other things while Cowboy does its work.

	cd $PBS_O_WORKDIR/

This line tells `qsub` to move into the directory that you submitted your script from. Now whatever commands happen after this point, it will be as if you submitted those commands to Cowboy from that directory. We can see that in this script we are loading the Mathematica module. Often people will create a master submit script and modify it for each specific job instead of writing a new one for each new job. Feel free to use this one as a template if you would like.

Submitting a Job
----------------

Enough talk, let's submit our job and see what happens. Open up the submit script with `nano` and change it so that it contains your email. Save, quit, and then use the following command to submit the script:

	qsub examplesubmitscript.sub

It will give a number. This is your job number and it allows you to track your job with the scheduler. Let's see how the job is doing:

	showq -u monkey

Shows all of your jobs that are on the queue. We can also see all the other jobs on the queue by leaving off the user name option:

	showq

Another command which is similar, but gives us just a little less information is:

	qstat -u monkey

Finally, if we want to cancel our job, we use:

	qdel 123456

This would remove my job from the queue if my job number was 123456.

Checking on Results
-------------------
Alright, did you get an email from Cowboy? Cowboy should have put your output into a file named by the submit script name followed by the job number. Simply move to the directory where you submitted the script from and have a look at the file to see what happened while your program was running on the compute nodes.

Congratulations, you are just about [finished]({{ site.url }}{{ site.baseurl }}/congratulations.html).
