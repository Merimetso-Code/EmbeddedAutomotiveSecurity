# Exercise 4 - Disassemble a ECU flash image

The goal of this execise is to disasemble a ECU Flash Image. To do this we will need to download and install the GNU PowerPC tool chain. The GNU PowerPC Tool Chain for Microsoft Windows 10 can be located at the following:

* [GNU PowerPC Tool Chain](https://gnutoolchains.com/powerpc-eabi/)

Once you have installed the GNU Tool Chain you should have somthing that look like the following:

```
c:\SysGCC\powerpc-eabi\bin>dir
 Volume in drive C has no label.
 Volume Serial Number is 70FA-A8D5

 Directory of c:\SysGCC\powerpc-eabi\bin

29/07/2021  17:36    <DIR>          .
29/07/2021  17:36    <DIR>          ..
29/07/2021  17:36           205,838 make.exe
29/07/2021  17:36           774,670 powerpc-eabi-addr2line.exe
29/07/2021  17:36           799,246 powerpc-eabi-ar.exe
29/07/2021  17:36         1,178,126 powerpc-eabi-as.exe
29/07/2021  17:36           773,134 powerpc-eabi-c++.exe
29/07/2021  17:36           773,134 powerpc-eabi-c++filt.exe
29/07/2021  17:36           772,110 powerpc-eabi-cpp.exe
29/07/2021  17:36            58,382 powerpc-eabi-elfedit.exe
29/07/2021  17:36             8,611 powerpc-eabi-embedspu
29/07/2021  17:36           773,134 powerpc-eabi-g++.exe
29/07/2021  17:36           770,062 powerpc-eabi-gcc-4.9.0.exe
29/07/2021  17:36            53,774 powerpc-eabi-gcc-ar.exe
29/07/2021  17:36            53,774 powerpc-eabi-gcc-nm.exe
29/07/2021  17:36            53,774 powerpc-eabi-gcc-ranlib.exe
29/07/2021  17:36           770,062 powerpc-eabi-gcc.exe
29/07/2021  17:36           462,350 powerpc-eabi-gcov.exe
29/07/2021  17:36         7,524,366 powerpc-eabi-gdb.exe
29/07/2021  17:36           840,718 powerpc-eabi-gprof.exe
29/07/2021  17:36         1,245,198 powerpc-eabi-ld.bfd.exe
29/07/2021  17:36         1,245,198 powerpc-eabi-ld.exe
29/07/2021  17:36           784,398 powerpc-eabi-nm.exe
29/07/2021  17:36           940,046 powerpc-eabi-objcopy.exe
29/07/2021  17:36         1,219,086 powerpc-eabi-objdump.exe
29/07/2021  17:36           799,246 powerpc-eabi-ranlib.exe
29/07/2021  17:36           438,798 powerpc-eabi-readelf.exe
29/07/2021  17:36         3,501,056 powerpc-eabi-run.exe
29/07/2021  17:36           776,206 powerpc-eabi-size.exe
29/07/2021  17:36           774,670 powerpc-eabi-strings.exe
29/07/2021  17:36           940,046 powerpc-eabi-strip.exe
              29 File(s)     29,309,213 bytes
               2 Dir(s)  754,428,510,208 bytes free

c:\SysGCC\powerpc-eabi\bin>
```

The tool set gives us the ability to compile and analyse software in the PowerPC format. The GCC compile will produce files in the [ELF](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format) format.  For this exercise you are goign to be analysing the following files.

* [ECU Flash Image](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise4.bin)
* [ECU ELF File](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise4.elf)

When analysing the Flash Image and ECU ELF File you may find teh following questions useful to consider:

* What strings are contained in the file and what does this tell us about the file.
* What functional dependancies exist within the files.
* What is the structure of the executable and what function does the executable make usse of.
* What does the disassemble of the file tells us.

## Useful Tools

To help you with your analysis you may find the following tools of use.

* powerpc-eabi-readelf.exe
    * This tool can be used examine the structure of an ELF executable. This includes the ability to examine the ELF headers and ELF sections.
* powerpc-eabi-strings.exe
    * This tool can be used to identify the strings contained within a single file. 
* powerpc-eabi-objdump.exe
    * This tool can used to disassemble the contents of an executable down into PowerPC machine code. 

## Other Tools

You may find other tools such as HEX editors useful in analysing the [Flash Image](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise4.bin) and the [ECU ELF File](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/Exercise4.elf)

* The [HxD](https://mh-nexus.de/en/hxd/) is a freeware hex editor that allows for the searching and analysis of file.

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
