pc41
====

Facilitating serial/USB connection to an HP-41. With this program you can
use your PC as a printer for an HP-41 (with Diego Diaz' USB41 module) or
transfer modules/data to/from an HP-41CL (with the serial interface):

Program created by Geir Isene (g@isene.com http://isene.com) to facilitate
connection between an HP-41 and a PC running  Linux/Unix/Mac OSX.

With this program and the USB41 module, you can use your PC as a printer
for the HP-41. USB41 module by Diego Diaz: http://www.clonix.org 

With this program and the serial interface to the HP-41CL replacement
board, you can transfer data/modules between a PC and an HP-41. HP-41CL by
Monte Dalrymple: http://www.systemyde.com

  SYNOPSIS: 

  pc41 [DEVICE] [OPTION]

  DEVICE:

  d=devicename
    Specifies the device name for the connection from the PC.

  OPTIONS:

  -h
    Displays the helpfile

  r=filename
    Read data from the HP-41 and save to "filename" (9600 baud)

  w=filename
    Writes "filename" from the PC to the HP-41 (4800 baud)
  

Make sure the program is "runable" (with "chmod a+x") and drop it in your
"bin" folder of choice and you are ready to go.

The program must be run as root to get access to the serial/usb port.

The program defaults to input from /dev/ttyUSB0, but you may specify
another input device by simply adding it as an argument to the program:

    pc41 d=/dev/ttyUSB1

Default usage is with the USB41 module. To use the program to transfer
data/modules using the HP-41, you need to provide one of two options:

    pc41 r=filename
    pc41 w=filename

With the option "r=filename", you READ data FROM the HP-41 and save it in
the file specified by "filename".

With the option "w=filename", you WRITE data from the file specified by
"filename" TO the HP-41.

Without the "r=" or "w=" options, the program expects input from an HP-41
with the USB41 module and acts as a printer.

Any printing from your HP-41 will go to Standard Out. To print whatever
comes from the HP-41 straight onto the screen, simply run the program:

    pc41

You can of course do all kinds of tricks on the PC side like piping the output
or redirect it to a file, etc.

To print a program on the HP-41 to the file "myprogram.txt" on the PC, do:

    pc41 > myprogram.txt

Except for ending the program with a "Control-C" on the PC, you may also print
the message "PREND", and the program will terminate (just enter "PREND" into
Alpha and do XEQ"PRA")

You must have Ruby installed as well as "ruby-serialport" (on Ubuntu or Debian,
do "sudo apt-get install ruby-serialport"). Alternatively you may install
ruby-serialport from RubyGems:

    sudo gem install ruby-serialport

The script will work just the same.

For Mac OS/X users, the usual device would be "/dev/tty.usbserial ". To
write the file "~/coolstuff.txt" from a Mac OSX computer to the HP-41CL
using the serial connector:

    pc41 d=/dev/tty.usbserial w=~/coolstuff.txt        

Version: 0.3 (2012-06-13)
License: Public domain
