# Exercise 5 - Reverse engineering functionality and finding bugs

The goal of this exercise is to explore how we can use various tools such as reverse engineering to find bugs and vulnerabilities in ECU firmware that makes use of the CAN bus. The GNU PowerPC Tool Chain for Microsoft Windows 10 can be located at the following:

* [GNU PowerPC Tool Chain](https://gnutoolchains.com/powerpc-eabi/)

In this exercise you are going to use the GNU Tool Chain to identify the functionality of the following:

* [Exercise5 ELF Binary](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise5.elf)

## Hints and Tips

The [Exercise5 ELF Binary](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise5.elf) has been created using S32DS for the MPC5748G Development Board. 



C:\Users\Andrew Blyth\Desktop>C:\SysGCC\powerpc-eabi\bin\powerpc-eabi-readelf.exe -h Exercise5.elf
ELF Header:
  Magic:   7f 45 4c 46 01 02 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, big endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           PowerPC
  Version:                           0x1
  Entry point address:               0x1000000
  Start of program headers:          52 (bytes into file)
  Start of section headers:          801884 (bytes into file)
  Flags:                             0x0
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         7
  Size of section headers:           40 (bytes)
  Number of section headers:         29
  Section header string table index: 28

C:\Users\Andrew Blyth\Desktop>

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
