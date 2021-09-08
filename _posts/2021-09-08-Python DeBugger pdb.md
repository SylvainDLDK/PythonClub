# pdb: Python DeBugger

I often wondered when/how to use the ["Debug" command](https://docs.spyder-ide.org/3/debugging.html) in the Spyder interface, and what was the [pdb module](https://docs.python.org/3/library/pdb.html) called by this command. 

Before going into the details of debugging options and the Python DeBugger (pdb) module, let's review typical situations that we want to debug:
- an [Error or Exception](https://docs.python.org/3/tutorial/errors.html) has been raised while running a script, resulting in a crash: the script did not run to completion.  
- a script ran to completion without raising any error, but its behavior is strange: unexpected output or incorrect plotting... 
- a GUI (Graphical User Interface) that you coded do not react correctly when you press some buttons or to some other events (incoming data...)
- communication with an instrument seems broken
- ...

Most of the time, we can find the origin of the problem and solve it by:
- using the [traceback](https://realpython.com/python-traceback/) that Python prints in your console when an exception is raised. Reading and understanding the traceback seems complicated at first, but you become extremely efficient at solving bugs when using it. I especially like the clickable links on the traceback that brings your cursor directly on the faulty line in the Editor. 
- when your script returns, your ipython console is available for you to explore variables that are suspect.
- breaking the code in smaller pieces, which you test one after another, usually goes a long way towards solving a bug. The "Run" command in Spyder's navigation bar contains helpful tools for this: 
	- F9 to run a single line or a selection of lines 
	- split a long code into several [cells](https://docs.spyder-ide.org/current/panes/editor.html#defining-code-cells) (using #%%), and run the cells one after another using Ctrl + Enter (or Shift + Enter). This should be familiar to you if you are used to work with Jupyter Notebooks. 

However, the above solutions do not work when:  
-  you work on a GUI and the ipython console is stuck in the infinite event loop of the application until you kill the application. The console is not available to explore variables.
- when the variables that you want to explore are in the local scope of a function, which you cannot access as the ipython console only knows the global variable. 

In such case, I find myself starting to use print() everywhere in the code. It always works, but after a lot of time and pain.  I will often have to print a lot of variables to find out where is the problem, and I cannot even manipulate these variables as easily as if there were accessible from a python console. For example, if I want to investigate an array a, I will: 
- print a few values to check their type print(a)
- print its shape print(a.shape)
- print min/max print(a.min(), a.max())
- ...
This is a lot of print() statement to write in the script. It would be much easier if the array would be directly available in the console, where I could explore it and manipulate it with the script methods that I am developing. 
