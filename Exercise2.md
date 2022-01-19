# Exercise 2 - Build your own ECU firmware (using SPC5 Studio)

The goal of this exercise is to Build/Install your own ECU firmware (using SPC5 Studio). The first stage of this is to download and install the S32 Power PC Design Studio. To achieve this please click on the following link and download and install the S32DS software.

* [SPC5 Studio](https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/spc5-software-development-tools/spc5-studio.html)

You may also want to download and access the Installation Guide and Release notes associated with SPC5 Studio. These can be found using the above link. Once SPC5 Studio has been installed then we can start to create out first firmware.

For this exercise you can create a project using one of the following two methods:

* Run the S32DS software and then using the following pull down menus create a project.
  * File -> New -> SPC5Studio Import Wizard
    * Select a Family -> SPC56
    * Select a Product Line -> P-Line
    * Select SPC560P-Disp -> NEXT
    * Then Select:
      * SPC56_Discovery -> FreeRTOS
      * Application Name: SPC560Pxx_RLA_FreeRTOS Serial Test

When you have installed the SPC5 Studio, then connect the SPC560P Development Board to your laptop. Once you have executed the SPC5 Studio software and created/loaded the project, then can you edit the main function in the file. In the main function you should see the following:
```c

```
Now edit the while loop and replace it with an infinite for loop. Within that for-loop define an 32-bit integer and then:
* Sets the integer to zero;
* Adds 32768 to it;
* Sets it to zero again;
* Subtract 1 from it.

Once you have down this compile project and download the project to the development board and reboot the developments board.

# Advanced Exercise 2

Once you have compiled and downloaded the project onto the development board then use the SPC5 Studio Debugger to step through the source code and execute it one command at a time. When debugging the software examine the variables and see how they change over time.

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
