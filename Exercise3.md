# Exercise 3 - Use JTAG to Snapshot a Device for Emulation

The goal of this exercise is to develop an understanding of JTAG and using JTAG to take a snapshot of the memory of a device. To this exercise we will make use of the Segger J-Link Software and Hardware.

* [Segger J-Link Software](https://www.segger.com/downloads/jlink/)
* [Segger J-Link Hardware](https://www.segger.com/products/debug-probes/j-link/models/j-link-edu/)

To start this exercise you will need to download and install the [Segger J-Link Software](https://www.segger.com/downloads/jlink/) on your laptop. To start this exercise you will need to connect the SPC560P-DISP development board to the power supply and turn the board on. Then you will need to connect the Segger J-Link Hardware to your Laptop and the Segger J-Link Hardware to the SPC560P-DISP development board via a JTAG connection. When connecting the the SPC560P Development Board to the J-Link please remember to:

* Connect GND on the SPC560P Development Board to GND on the J-Link (This is so we can measure digital Zero)
* Connect VCC on the SPC560P Development Board to VREF on the J-Link (This is so we can measure digital One)
* On the SPC560P Development Board remember to use the X2 JTAG interface

You can identify the Pin-Outs on the SPC560P Development Board and the pin-outs on the J-Link via the following:

* [SPC560P Development Board - JTAG Pin Outs](2520506.jpg)
* [J-Link - JTAG Pin Out](PinOut.png)

Once you have connect all the hardware components together you should run the J-Link software on your laptop. When running the J-Link software you will need to use the connect command to configure the J-Link software/hardware. When using the conned command you will need to specify the CPU type (SPC560P50) and then just select the default options.  

## Directed Reading.

For those students interested in using JTAG I would recommend the following Books.

* [Hardware Security: A Hands-on Learning Approach](https://www.amazon.co.uk/Hardware-Security-Hands-Learning-Approach/dp/0128124776/ref=sr_1_11?dchild=1&keywords=JTAG&qid=1628006748&s=books&sr=1-11)
* [Practical Hardware Penetration Testing](https://www.amazon.co.uk/Practical-Hardware-Pentesting-attacking-protecting/dp/1789619130/ref=sr_1_1?dchild=1&keywords=Practical+Hardware&qid=1628006813&s=books&sr=1-1)
* [Practical IoT Hacking](https://www.amazon.co.uk/Practical-IoT-Hacking-F-Chantzis/dp/1718500904/ref=pd_bxgy_1/259-6778613-4386513?pd_rd_w=y6uo1&pf_rd_p=c7ea61ca-7168-47e3-9c8b-d84748f5b23c&pf_rd_r=K7H7Y7TTR9XDB064ZR99&pd_rd_r=b74196ca-110d-447c-8050-2e45cc971acb&pd_rd_wg=GrbLa&pd_rd_i=1718500904&psc=1)
* [The Boundary-Scan Handbook](https://www.amazon.co.uk/Boundary-Scan-Handbook-Kenneth-Parker-2015-11-12/dp/B01JXUQYJI/ref=sr_1_2?dchild=1&keywords=boundary+scan&qid=1628006876&s=books&sr=1-2)

For those students interested in using JTAG I would recommend the following Links.

* [Introduction to JTAG](https://en.wikipedia.org/wiki/JTAG)
* [JTAG Explained](https://blog.senr.io/blog/jtag-explained)

For those students interested in using JTAG I would recommend the following Videos.

* [What is JTAG](https://www.youtube.com/watch?v=TlWlLeC5BUs)
* [JTAG TAP Controller](https://www.youtube.com/watch?v=PhaqHKyAvR4)

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
