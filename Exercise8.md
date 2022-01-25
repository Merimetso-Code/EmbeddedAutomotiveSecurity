# Exercise 8 - FlexRay and CAN BUS

The goal of this exercise is to use the GDB command line debugger to be debug a CAN Application. The following CAN application should be downloaded and installed on an SPC560P development board.

* [EXERCISE 8 - Serial Bus Application](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE8.zip)

Connect your laptop to the SPC560P Development Board, via a USB connection, and compile the downloaded the application. You should then step through the application setting breakpoints, and explore the stack and registers using the Universal Debugger Engine (UDE).  You should step through the following functions using break points and explore how variables can be set to trigger behaviour. In compute.h the 'compute' function is defined along with the 'MAXCOUNT' constant that is used in the 'main' function.

```c
//
#define MAXCOUNT 64
//
int compute(int, int);
```

In the fine HH the implementation of the 'compute' function is defined.

```c
//
int compute(int valA, int valB) {
	//
	int valC = 0;
	//
	if (valB == 0) { valB= 1; } else { valB = 0; }
	//
	valC = valA + valB;
	//
	return valC;
}
```

In the 'main' function the compute function is used within a for loop.

```c
for(counter=0; counter < MAXCOUNT; counter++) {
  dataA = compute(dataA, dataB);
}
```

The main function also make use of the following functions to read and transmit data on the CAN bus.
```c
//
while (can_lld_transmit(&CAND1, 1, &txmsg) == CAN_MSG_WAIT) {
  // Do nothing
}
//
if (can_lld_receive(&CAND1, 1, &rxmsg) == CAN_MSG_OK) {
  // Process the data
}
```

You should explore/debug the functions described above to create an understand of how the application behaves:

* What is that data that is passed to/from the 'can_lld_transmit' and 'can_lld_receive' functions?
  * Where is the data stored and what happens when I modify this data?
  * What does the stack look like when these functions are invoked?
* What is that data that is passed to/from the 'compute' function?
  * Where is the data stored and what happens when I modify this data?
  * How can I modify the behaviour of the for loop used to invoke the 'compute' function?
  * Within the function 'compute', what happens when I change the value of valB to 255?
  * what happens if I modify the machine code so that when valB is equal to 0, then the value of valB is set to 1024?
  * What does the stack look like when these functions are invoked?

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
