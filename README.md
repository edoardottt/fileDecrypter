# fileDecrypter :lock:
**0010101010101001010 ---- Simple C file decrypter ---- 1010100101010101010001**

**Disclaimer**: This was a part of a University project (Operating System course), not a serious decrypter. 

Description :mega:
--------

fileDecrypter is able to read and edit binary files with a certain format.

More in detail, the program takes as input 3 arguments: the name of a file *fin*, the name of a file *fout* and a string *s*.  
The file *fin* is a binary file of an obfuscated text, in which, for each memorized character, a 16 bit number is used, composed as follows: 0xy0<sub>16</sub>, where xy<sub>16</sub> is the ASCII code of the character.  
The program must execute the command `/bin/sed -e s`, making sure that the standard input of this command is the content of the defluxed file (that is, removing the 4 bits to zero before and after each character).

The program then takes the result of the above command (on standard output), replaces (adding 4 bits to zero before and after each character) and write the result of this re-obfuscation on fout. Any written sed on standard error is ignored.

Only the following errors can occur:

- The program does not start with the required topics. 
The program then ends with exit status 10 (without performing any action), and writing on standard error:
            
            Usage: p file sed script, where p is the name of the program itself.
    
- The file does not exist or is not accessible. 
The program then ends with exit status 20 (without performing any action), and writing on standard error:

            Unable to r file f because of e, where e is the system string
    
which explains the error and r is read from if f is not accessible for reading, or write to if it is not accessible for writing.

- The file read is not well formatted: bits at 0 are missing in some positions where they should be.
In this case, it ends with an exit status 30, generating the output up to the wrong byte excluded and writing on standard error:

            Wrong format for input binary file f at byte d
    
where d is the byte number (starting from 0) where the error occurs.

- Any other system call fails. The program ends with exit status 100 (without performing any other action), and writing on standard error:

            System call s failed because of e
    
where e is the system string that explains the error and s is the system call that failed.

Usage 🔧
-------

- `gcc decrypter.c -o decrypter`
- `./decrypter`

Download 📡
-------

`git clone https://github.com/edoardottt/fileDecrypter.git`


If you liked it drop a :star:
--------

https://www.edoardoottavianelli.it for contact me.

                                                                   Edoardo Ottavianelli

