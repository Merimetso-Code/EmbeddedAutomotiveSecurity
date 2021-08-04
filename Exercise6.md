# Exercises 6 - Mapping and understanding attack surface

The goalof this exercise is t get us to think about how we might exececute a attack against an ECU. In this exercise we are going to make use of both of the MPC5748G development boards. Take the two MPC5748G development boards and wire then together so that their CAN buses are connected and they can communicate together via the CAN Bus. On MPC5748G development board 1 we are goiing to execute a CAN BUS reciece Program and and MPC5748G development board 2 we are goiing to execute a CAN BUS transmit Program.

* [MPC5748G Development Board 1](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Transmit.7z)
* [MPC5748G Development Board 2](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Recieve.7z)

Once you have programmed both boards so that they are executing the required software we can now examine the system from a holistic perspective for vulnerabilities. In partcular we examining the attack surface fo a system you shoudl ask the following questions:

* Does teh hardware contain any 
    ** data access ports such as USB, CAN, LIN and Ethernet and are these data ports used.
    ** debug/programming ports such as I2C, SPI and JTAG and how can these ports be accessed.
* 
 
## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
