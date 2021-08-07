# Exercise 8 - FlexRay

The goal of this excercise is to use the GDB command line debugger to be debug a FLEX CAN Application. The following FLEX CAN application should be downloaded and installed on an MPC5748G development board.

* [EXERCISE 8 - FLEX CAN Bus Application](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE8.7z)

On the Windows PC connected to the  MPC5748G development board, via a USB connection, running the [EXERCISE 8 - FLEX CAN Bus Application]() and S32DS compile and download the application to the MPC5748G development board. Once this has been achieved, click the debug button for the Z4_0 core in the S32DS environment. You should step through the following functions usinfg break points and explore how variables can be set to trigger behaviour.

```c
/************************************ Select ********************************************/
int addmu(uint32_t index){
	return index + 8;
}
/************************************ Select ********************************************/
int select(){
	uint32_t xspc_0 = 1;
	uint32_t xspc_1 = 0;
	uint32_t loop_0 = 0;
	for (loop_0 = 0; loop_0 < 7; loop_0++) {
		xspc_1 = xspc_1 + addmu(xspc_0);
		xspc_0++;
	}
	return xspc_1;
}

/************************************ Main **********************************************/
int main(void)
{
 	uint32_t CAN_msg_count = 0;
 	uint32_t counres = 0;
	xcptn_xmpl ();         	/* Configure and Enable Interrupts 	     		*/
	peri_clock_gating();   	/* Configure gating/enabling peripheral clocks(CANs) 	*/
	                       	/* Configuration occurs after mode transition 		*/
	system160mhz();        	/* sysclk=160MHz, dividers configured, mode trans	*/
	initCAN_0_rx();     	/* Initialise FlexCAN 0 & one of its buffers for receive*/
	while (1) {
	  ReceiveMsg();       	/* Transmit one message from a FlexCAN 0 buffer 	*/
	  CAN_msg_count++;      /* Increment CAN message counter 			*/
	  SIUL2.MSCR[PA7].B.OBE = 1;  /* Pad PA7 (7): OBE=1. On EVB enable low DS5 LED 	*/
	}
	counres = select();
	return 0;
}
```

## Command Line Debugging

Should you want to explore command line debugging you can explore using the GNU debugger to:

* Access Registers
* Access Memory

Once the debugger is invoked in S32DS you can connect to the development board via the following GDB command:

```
(gdb) target remote localhost:7224
```

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
