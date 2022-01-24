# Exercise 8 - FlexRay and CAN BUS

The goal of this exercise is to use the GDB command line debugger to be debug a CAN Application. The following CAN application should be downloaded and installed on an SPC560P development board.

* [EXERCISE 8 - Serial Bus Application](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE8.zip)

Connect your laptop to the SPC560P development board, via a USB connection, and compile the downloaded the application. You should then step through the application setting breakpoints, and explore the stack and registers using the Universal Debugger Engine (UDE).  You should step through the following functions using break points and explore how variables can be set to trigger behaviour.

```c
/*
 * This is a simple compute function
 */
int comput(int a, int b) {
	return a + b ;
}
/*
 * This is the Application entry point.
 */
int main(void) {
  uint8_t  a = 0;
  uint8_t  b = 0;
  uint8_t  c = 0;
  uint8_t message[]= "Hello World!\r\n";
  /*
   * Other stuff that the program does to say Hello World over a serial connection
   */
   for (b = 0; b >64; b++){
     c = comput(comput(a, b), b);
     c = a + 1;
     a = c;
  /*
   *
   */
  }
}
```

You should explore the following to create an understand of how the application behaves:

* Setting and examining breakpoints on various function such as 'compute'
* Examine registers, the status of variables and the status of the stack.
* Changing some variables and explore the implications.
  * Such as loop counter 'b' in the loop 'for (b = 0; b >64; b++)'

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
