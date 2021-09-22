---
title: "Debugging in Python"
description: "The Python DeBugger (pdb) module: why, when and how to use it?"
layout: post
toc: true
comments: true
hide: false
search_exclude: true
author: "<a href='https://github.com/SylvainDLDK'>Sylvain DLDK</a> "

categories: [spyder, pdb]
---

I often wondered when/how to use the ["Debug" command](https://docs.spyder-ide.org/3/debugging.html) in the Spyder interface, and what was the [pdb module](https://docs.python.org/3/library/pdb.html) called by this command. So I finally decided to look seriously at this tool and make it this week's topic. 

I only use Python within [Spyder](https://www.spyder-ide.org/) or [Jupyter Lab](https://jupyter.org/index.html), and debug mainly in Spyder, so I will focus on tools to debug when writing and running scripts within Spyder. However, most concepts and tools described below are not at all limited to Spyder.   

# Types of bugs I often encounter

Before going into the various debugging options and the Python DeBugger (pdb) module, let's review typical situations that we need to debug:
- an [Error or Exception](https://docs.python.org/3/tutorial/errors.html) has been raised while running a script, resulting in a crash: the script did not run to completion.  
- a script ran to completion without raising any error, but its behavior is strange: unexpected output or incorrect plotting... 
- a GUI (Graphical User Interface) that I coded do not react correctly when pressing some buttons or to some other events (incoming data...)
- communication with an instrument seems broken
- ...

# Debugging without pdb

Most of the time, we can find the origin of a problem and solve it by:
- using the [traceback](https://realpython.com/python-traceback/) that Python prints in your console when an exception is raised. Reading and understanding the traceback seems complicated at first, but you become extremely efficient at solving bugs when using it. I especially like the clickable links on the traceback that brings your cursor directly on the faulty line in the Editor. 
- when a script returns, the ipython console is available for us to explore variables that are suspect.
- breaking the code in smaller pieces, and testing them one after another, usually goes a long way towards solving a bug. The "Run" command in Spyder's navigation bar contains helpful tools for this: 
	- F9 to run a single line or a selection of lines 
	- split a long code into several [cells](https://docs.spyder-ide.org/current/panes/editor.html#defining-code-cells) (using #%%), and run the cells one after another using Ctrl + Enter (or Shift + Enter). This should be familiar for those familiar to with Jupyter Notebooks. 

# Where pdb seems to be a powerful tool

However, the above solutions do not work when:  
-  working on a GUI and the ipython console is stuck in the infinite event loop of the application until the app is closed: the console is not available to explore variables.
- when the variables that we want to explore are in the local scope of a function, which we cannot access as the ipython console only knows the global variables. 

In such case, I find myself starting to use print() everywhere in my code. It always works, but after a lot of time and pain.  I will often have to print a lot of variables to find out where is the problem, and I cannot even manipulate these variables as easily as if there were accessible from a python console. 

For example, if I want to investigate an array a, I will check: 
- a few values to check their type print(a)
- its shape print(a.shape)
- min/max print(a.min(), a.max())
- ...

This is a lot of print() statements to write in the script. It would be much easier if the array would be directly available in the console, where I could explore it and manipulate it with the script methods that I am developing. 

This is where the Python DeBugger pops in. 

# Learning to use pdb

See links below for now...

# Links

- [pdb doc](https://docs.python.org/3/library/pdb.html) by python
- [Tutorial to pdb](https://realpython.com/python-debugging-pdb/) by RealPython
- [Understanding the python traceback](https://realpython.com/python-traceback/) by RealPython
- [Debugger tutorial](https://docs.spyder-ide.org/current/panes/debugging.html) by Spyder
- [Introduction to pdb](https://pythonconquerstheuniverse.wordpress.com/2009/09/10/debugging-in-python/) by Steve Ferg
- [Debugging Python programs in Spyder](https://wiki.math.ntnu.no/anaconda/debugging) by Kristian Hove
- [Errors and Debugging](https://jakevdp.github.io/PythonDataScienceHandbook/01.06-errors-and-debugging.html) by Jake VanderPlas
- [5 Ways of Debugging with IPython](https://switowski.com/blog/ipython-debugging) by Sebastian Witowski
- [Debugging with Spyder](https://fangohr.github.io/blog/spyder-the-scientific-python-development-environment.html#debugging) by Hans Fagohr
