# Exercise 2 - Build your own ECU firmware (using S32 Design Studio)

The goal of this exceise is to Build your own ECU firmware (using S32 Design Studio). The first stage of this is to download and stann the S32 Power PC Design Studio. To acheive this please click on the following link and download and install the S32DS software. Please rember that when installing the S32DS software you will need to access the Licence Keys tab and web page and obtain a licence key.

* https://www.nxp.com/design/software/development-software/s32-design-studio-ide/s32-design-studio-for-power-architecture:S32DS-PA?&tab=Design_Tools_Tab

You may also want to download and access the Installation Guide and Release notes associated with S32 DesigN Studion. These can be found using the above link. Once S32 Design Studion has been installed then we can start to create out first firmware.

For this exercise you can create the S32DS project using one of the following two methods:

* Run the S32DS software and then using the following pull down menus create a project.
  * File -> New -> S32DS Project From Example 
  * Select the Hello Project (Turns on the DS4, DS6 and DS8 LED using differenet cores) from the S32DS Example projects
* Download the following and then uncompress and open the project.
  * [Exercise 2 - S32DS Project](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE2.7z)

When you have installed the S32DS studio, then connect the MPC5748G Development Board to your laptop. Once you have executed the S32DS software and created/loaded the project, then can you edit the main function in the file hello_Z4_1.c. In the main function you should see teh following:
```c
int main(void)
{
        xcptn_xmpl ();                  /* Configure and Enable Interrupts                    */
        memory_config_16mhz();          /* Configure wait states, flash master access, etc.   */
        SIUL2.MSCR[PA10].B.OBE = 1;     /* Pad PA10 (10): OBE=1. On EVB active low DS4 LED    */
        clock_out_FIRC();               /* Pad PG7 = CLOCKOUT = FIRC / 10                     */
        while(1);
        return 0;
}
```
Now edit the while loop and replace it with an infinite for loop. Within that for-loop define an 32-bit integer and then:
* Sets the integer to zero;
* Adds 32768 to it;
* Sets it to zero again;
* Subtract 1 from it.

Once you have down this compile project and download the project to the development board and reboot the developmente board.

# Advanced Exercise 2

Once you have compiled and downloaded the project onto the development board then use the S32DS debugger to step through the source code and execute it one command at a time. When debugging the software examine the variables and see how they change over time.

# Tips and Hints
Information and help on progamming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
