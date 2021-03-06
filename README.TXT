
                              Tape Utilities
                             ----------------
                     Z80 Snapshot to TZX Tape Converter
                                   v1.2

                               by Tomaz Kac

                        .SNA support by Simon Owen

  This program will let you convert any Z80 or SNA Snapshot to a TZX Tape
file. This means that you will be able to play that file into a real ZX
Spectrum (or an  emulator) without any special hardware. Both 128k and 48k
snapshots (all versions) are supported. .SNA support was added in version
1.2 by Simon Owen. You can use any other snapshot convertor to convert
different (non-supported) formats to .Z80 format (preffered).
  There have been a few utilities like this, but I felt this needed doing. The
reasons are because most of the previous utilities lack the support for
customizing the resulting TZX file or had too many bugs. TAPER has a really
nice support for the conversion from Z80 to TZX format, unfortunetly it has
so many bugs that it is practically unusable. I could bug-fix it, but it would
take way too much time and it needs DOS to run (Doesn't run on XP !).
  With this utility you are able to customize your TZX file in several ways.
You can change the speed of loading (from standard speed to 400%), all
messages that you see while loading can also be changed and added. Also you
can supply a custom external loading screen. I have gone through a great deal
of testing (around 300 Z80 snapshots which didn't work with TAPER all work
with this).

  There are still some snapshots which rely on the last line on screen to be
original - this line is corrupted because it is used to store all registers,
etc. These include games like Back To Skool and Skool Daze. You will have to
snapshot these at a later time (in-game for instance). Unfortunetly nothing
can be done here...

  There are several ways you can customize your TZX file. You can change the
Loading: Name to anything you want ( 8 Characters only ). You can also change
the Game Name that is shown before the SCREEN$ is loaded. Also you can add
two extra lines of info on the bottom of the screen if you want.

  The converter takes care of several issues when loading the snapshot :
  
- Loader for 48k and 128k Snapshots is the same. Only part that is different
  is the AY and 128k Paging registers setup.
- Each page is checked if it is empty - if so then it is not loaded at all.
- Each page is compressed and if its length is smaller than original size
  it is kept compressed. Also an additional check is done to see if the
  decompression procedure doesn't overwrite the compressed source !
- The first page or the custom loading SCREEN$ is always loaded compressed
  and is displayed instantly.
- If custom loading screen is present then the last page is always loaded
  decompressed so the loading of the screen looks nice (backward loading).
- In the end the 768 bytes long block is loaded with Normal ROM routines,
  and only if it is needed. This overwrites the are where the loader and
  register info is kept before it is moved into the last line of the
  screen area.

  *LICENCE*
  
  Because some parts of the program are taken from TAPER (by Martij v.d.
Heide - THANX for letting me use the code!) the licence of this program is
the same - GPL General Public License. The sources are distributed within
the archive !
  
  *COMMAND LINE SYNTAX*

Z802TZX Filename [Options]

Options:

 -v    Verbose Output (Prints Info on conversion, otherwise NO output !)
 -s n  Loading Speed (n: 0=1500  1=2250  2=3000  3=6000 bps) Default: 3
       If you are saving to tape then use 3000 Baud (2)
 -b n  Border (0=Black 1=Blue 2=Red 3=Magenta 4=Green 5=Cyan 6=Yellow 7=White)
       This is the final colour of the border when the game is loaded. Also
       this is the last attribute line colour and the loading stripes colour !
 -r    Use Bright Colour when filling in the last attribute line
 -$ f  Use External Loading Screen in file f (.scr 6912 bytes long file)
 -o f  Use f as the Output File (Default: Input File with .tzx extension)
 -l s  Use String s as the ZX Loader Name (Loading: name) Up To 8 Chars!
       Otherwise this is taken from first 8 characters of Filename !
 -g s  Use String s as the Game Name (Shown when Loading starts)
       Otherwise taken from Filename and formatted a bit !
 -i1 s Show a line of info when loading (first line)
 -i2 s Show another line of info when loading (second line)

 Strings (s) can be Up To 32 chars long.
 Use '~' as (C) char for Game name and Info lines.
 If no Border Colour is selected then it will be gathered from the snapshot
 file.
 
 Filename can have an extension of .z80 or .sna !

HISTORY:  1.0  - * First Public release
          1.1  - * Changed the Timing for 6000 baud tapes. The 0-bit pulse
                   changed from 195 to 200 and 1-bit from 390 to 400.
                   Works fine now on all emulators and real ZX Spectrums.
          1.2  - * Added support for .SNA snapshots (both 48k and 128k
                   flavours are supported) - coded by Simon Owen !

  My email is   tomcat@sgn.net   ... mail me if you have any problems
with this program or would like to see some things added.

                                                                            TC
