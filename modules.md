---
layout: tutorial
title: Modules
---


Available Software
------------------
We now know how to use Cowboy, but what good is using a supercomputer if we cannot use the software on it? Windows has the Start Menu and Macintosh OS has the launch bar, but how do we find out what programs or software are available on Cowboy when all we have is the command prompt? The answer is modules. Modules are an extremely powerful system that allows multiple users with different versions of software all to use the same machine at the same time, and it's how we will be using the software on Cowboy. First, it would be nice to know what software Cowboy has available for us to use:

	module avail

We get output looking something like this:

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

Here we have a table listing all the software installed on Cowboy. Notice there are two general categories: Compilers, and Applications. Compilers are used by users who are writing their own code, while Applications work the exact same way as Applications in Windows or on a Macintosh (except no GUI). Look through the list and see if you can find `mathematica.` There are two entries: `mathematica/9.0.1` and `mathematica/10.0.0`. That's because there are two different versions of Mathematica installed on Cowboy and users are able to use either one. Next notice that some of the modules have a `(D)` next to them. Since there are multiple versions of each piece of software, certain versions are designated as default. In the case of Mathematica, if the user tells the computer to load Mathematica, but doesn't tell it which version to load, it will automatically load version 10.0.0. Finally, notice the word `--More--` at the bottom of the screen. The computer is telling us that the list keeps going. We can scroll down the list by hitting either enter (to go one line down) or space (to go one page down). Go ahead and scroll through until you get to the bottom of the list (your prompt will come back once the list has finished).

Spider
------
Once we reach the bottom of the list, we see that the module system has given us this helpful message:

	Use "module spider" to find all possible modules. 
	Use "module keyword key1 key2 ..." to search for all possible modules matching any 
	of the "keys". 

The message is letting us know about a tool that is similar to `module avail`, but has many more features than just listing installed software. Let's give it a try:

	module spider

Notice now we get the list of installed software, but this time each piece of software has a brief description that tells us what each piece of software is. Instead of scrolling to the bottom of the list type `q` to exit the list. This time try:

	module spider mrbayes

We are given a brief description of a piece of software called MrBayes. We can see that there are several versions and if we want more detailed information about one of the specific versions, then we will need to do a search for that specific version. Lets do that (remember up arrow and then modify the command if you want to save typing):

	module spider mrbayes/3.2.2-openmpi-intel

Now we are presented with a detailed description and help specific to that particular version of MrBayes. This is especially useful if we want to see whether or not the latest version of MrBayes has been installed on Cowboy. If you don't see the version of software that you need for your research and are an advanced user feel free to install the software in your home directory. Otherwise, you can contact us and we will be more than happy to install it for you. You can also see a current list of the software in installed on Cowboy [here][cowboysoftware].

[cowboysoftware]: https://github.com/OSU-HPCC/module-list/tree/master/availablesoftware

Using Software
--------------

In order to use the software on Cowboy we need to 'load' the software module. We can see what software we have loaded by using the following command:

	module list

We get an error message because we haven't loaded any software yet. Let's try Mathematica:

	module load mathematica

Now when we use module list we get the following:

	1) mathematica/10.0.0

which tells us that we are ready to use Mathematica. As a reminder, please remember that we are still in the login node and jobs should never be run from here. Instead submit the job to the scheduler which we will explain in the next section. Now let's get rid of Mathematica and instead load MrBayes:

	module rm mathematica
	module load mrbayes

Now when we use `module list` we see the following:

	1) mrbayes/3.2.2-openmpi-intel    2) openmpi-1.4/intel    3) beagle/1.0

Wait a minute, why are there so many modules? Didn't we just load MrBayes? The beauty of modules is that it automatically loads MrBayes and any other software that MrBayes depends on to run. Now, if I want to go back to Mathematica there is actually a shortcut that I can use instead of using `module rm` and then `module load`:

	module swap mrbayes mathematica

Let's reload MrBayes:

	module load mrbayes

Now we have both Mathematica and MrBayes loaded. Feel free to use `module list` and check it out. When we are done and we want to get rid of all of our modules. We can use the following command to unload all of our modules:

	module purge

Now that you are a module expert, it's time to learn about [submit scripts]({{ site.url }}{{ site.baseurl }}/submitscripts.html).
