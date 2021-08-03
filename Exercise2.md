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

Once you have executed the S32DS software and created/loaded the project, then can you edit the main function in the file hello_Z4_1.c. In the main function 
```c
int main(void)
{
        xcptn_xmpl ();              /* Configure and Enable Interrupts */

        memory_config_16mhz();          /* Configure wait states, flash master access, etc. */

        SIUL2.MSCR[PA10].B.OBE = 1;  /* Pad PA10 (10): OBE=1. On EVB active low DS4 LED */

        clock_out_FIRC();           /* Pad PG7 = CLOCKOUT = FIRC / 10 */

        while(1);

        return 0;
}
```
