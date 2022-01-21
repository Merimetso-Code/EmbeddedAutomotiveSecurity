# Exercise 8 - FlexRay and CAN BUS

The goal of this exercise is to use the GDB command line debugger to be debug a CAN Application. The following CAN application should be downloaded and installed on an SPC560P development board.

* [EXERCISE 8 - CAN Bus Application](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE8.7z)

On the Windows PC connected to the SPC560P development board, via a USB connection, running the [EXERCISE 8 - CAN Bus Application]() and compile and download the application to the SPC560P development board. You should step through the following functions using break points and explore how variables can be set to trigger behaviour.

```c

```

## Command Line Debugging

Should you want to explore command line debugging you can make use of the GNU debugger to:

* Access Registers
* Access Memory

Once the debugger is invoked in SPC5 Studio you can connect to the development board via the following GDB command:

```
(gdb) target remote localhost:7224
```

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
