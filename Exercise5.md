# Exercise 5 - Reverse engineering functionality and finding bugs

The goal of this exercise is to explore how we can use various tools such as reverse engineering to find bugs and vulnerabilities in ECU firmware that makes use of the CAN bus. The GNU PowerPC Tool Chain for Microsoft Windows 10 can be located at the following along with Radare2.

* [GNU PowerPC Tool Chain](https://gnutoolchains.com/powerpc-eabi/)
* [Radare 2](https://rada.re/n/)

In this exercise you are going to use the GNU Tool Chain to identify the functionality of the following:

* [Exercise5 ELF Binary](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise5.elf)

## Hints and Tips

The [Exercise5 ELF Binary](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise5.elf) has been created using SPC5 Studio for the SPC505P-DISP Development Board. The ELH Header for Exercise 5 is as follows, and from this we can see that it is a Power PC 32 Bit Big Endian File.  


```
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
```

Once you have statically reversed engineering the Exercise 5 Elf file then you may wish to download the following project that we used to create the Exercise 5 Elf and validate your findings. After you have downloaded the project, compile it and flash it to the SPC550P Development Board. When reverse engineering key questions to focus on are:

* What is the role/function of the software, What purpose does it fulfil?
* What function is the executable making use of and are there any debug symbols contained in the file?
* What strings/text-data is contained in the file and what does this tells us about the executable?

Then you can use the SPC5 Studio to execute the Elf file and validate your finds.

* [Exercise 5 ELF Project](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE5.7z)

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
