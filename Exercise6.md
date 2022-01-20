# Exercise 6 - Mapping and Understanding Attack Surface

The goal of this exercise is to get us to think about how we might execute an attack against an ECU. In this exercise we are going to make use of the SPC560P-Disp Development Board. On SPC560P-Disp Development Board we are going to execute a CAN BUS receive/transmit program.

* [SPC560P-Disp Development Board]()

Please note that for the following project we are making use of the Z4_0 core and that source code for this project can be located under that core. So for the CAN bus receive project we should have the following:
```

```

And for the CAN bus transmit project we should have the following
```

```

Once you have programmed both boards so that they are executing the required software we can now examine the system from a holistic perspective for vulnerabilities. In particular, we examining the attack surface for a system you should ask the following questions:

* Does the hardware contain any
    * data access ports such as USB, CAN, LIN and Ethernet and are these data ports used.
    * debug/programming ports such as I2C, SPI and JTAG and how can these ports be accessed.
* Does the software contain any vulnerabilities, such as
    * Can I write more that 8 bights of data to the CAN bus
    * I am using vulnerability functions such as strcpy()
    * Can I modify the data that is being transmitted over the CAN bus

## Advanced Topics

If you have an oscilloscope or a logic analyse then you may wish to mount a man in the middle attack and observe and analyses the data in the CAN Bus. Questions that you might like to answer are:

* What is the data that is being transmitted over the CAN bus?
* At what speed is the data being transmitted?

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
