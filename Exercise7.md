# Exercise 7 - Reverse engineering functionality and finding bugs (continued)

The goal of this exercise is to use the kill chain in analysing the software for the ECU and developing an exploit. The two stages that we are going to explore in this exercise are:

* Reconnaissance
* Weaponisation

![Cyber Kill Cain](KillChain.png)

So, to start with download the compressed package and uncompress it.

* [Exercise 7 - FreeRTOS Serial Application](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE7.zip)

This tutorial is structured in two parts. In the first part you are required to perform Reconnaissance on the software for the SPC650P ECU, and the second part you will be required to validate the exploit.  

* Stage 1 - Reconnaissance
  *  Stag 1 begins with the analysis of the following FreeRTOS code. Your analysis should focus on the main function and the tasks that the RTOS application creates. You are required to identify under what conditions an error/vulnerability can be triggered.
```
C:\SPC5Studio-6.0\workspace\SPC560Pxx_RLA FreeRTOS SERIAL Test Application for Discovery>dir

Directory of C:\SPC5Studio-6.0\workspace\SPC560Pxx_RLA FreeRTOS SERIAL Test Application for Discovery

21/01/2022  11:14    <DIR>          .
21/01/2022  11:14    <DIR>          ..
21/01/2022  11:14             8,358 .cproject
21/01/2022  11:14    <DIR>          .dep
21/01/2022  11:13             1,043 .project
21/01/2022  11:14    <DIR>          .settings
21/01/2022  11:13               164 .spc5project
21/01/2022  11:14             4,352 application.ld
21/01/2022  11:41    <DIR>          build
21/01/2022  11:14    <DIR>          components
21/01/2022  11:13            70,033 configuration.xml
21/01/2022  11:41             2,856 main.c
21/01/2022  11:14             4,732 Makefile
21/01/2022  11:14               165 patch.xml
21/01/2022  11:14    <DIR>          pclint
21/01/2022  11:13               222 readme.txt
21/01/2022  11:13    <DIR>          source
21/01/2022  11:14    <DIR>          UDE
21/01/2022  11:13               428 user.mak
             10 File(s)         92,353 bytes
              9 Dir(s)  726,936,666,112 bytes free

C:\SPC5Studio-6.0\workspace\SPC560Pxx_RLA FreeRTOS SERIAL Test Application for Discovery>
```  

* Stage 2 - Weaponisation
  *  For Stag 2 you are required to Weaponise the error/vulnerability identified in Stage 1. To achieve this you will need to make use of the SPC560P development board. On SPC560P Development Board A you will need to download and install the [Exercise 7]() and use the the SPC5 Studio. I would suggest that you validate the vulnerability via debugging the application SPC560P Development Board A to ensure that the vulnerability is correctly triggered.

For the RTOS Serial transmit/receive project is as follows.
```c
/* Include required files                               */
uint8_t message_task1[]= "Task1...\r\n";
uint8_t message_task2[]= "Task2...\r\n";
uint8_t mess1[30] ="\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0";
uint8_t mess2[]= "Task....\r\n";

/* Task One Definition
    Copy message_task2 -> mess2
    Copy mess1 -> mess2
*/

/* Task Two Definition                                  */

int main(void) {
  /* Initialise data, variables and interrupts          */

  /* Create/Run Task 1                                  */
  xTaskCreate( vTaskOne,
               (const char * const)"task #1",
               configMINIMAL_STACK_SIZE,
               NULL,
               tskIDLE_PRIORITY + 1,
               NULL );

  /* Create/Run Task 2                                  */
  xTaskCreate( vTaskOne,
               (const char * const)"task #1",
               configMINIMAL_STACK_SIZE,
               NULL,
               tskIDLE_PRIORITY + 1,
               NULL );

  /* Start the FreeRTOS scheduler */
  vTaskStartScheduler();

  return 0;
}
```
## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>

# Tips and Hints
For help on this exercise:
* Look at the buffers used to copy data for Task 1
* What data/characters are in those buffers?
* What happens when to change the data in the buffers?

Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
