# EverDrive-Packs-Lists-Database

The EverDrive Packs Lists Project is an archival research initiave
with the goal of allowing users to build real-hardware optimized ROM
packs based on suggested file/folder layouts compiled by SmokeMonster.

Because most flash-carts require specific ROMs and fixes, it is a
monumental task to compile 100% complete/working setups, and is often
beyond the capabilities of any one person. Thousands of hours have
been invested in the *SmokeMonster DataBases* (or SMDBs) of this
project with the goal of 100% complete, 100% working real-hardware
compatible arrangements of the highest quality ROM dumps. File
hierarchies are shared via SMDB text files which contain all of the
information needed to identify and sort files.

What's in a SMDB file? A SMDB file generated by the `parse_pack`
script is an archival text record describing exact files (using hash
values [SHA256
hash](https://en.wikipedia.org/wiki/Secure_Hash_Algorithms), SHA1, MD5
and CRC32) and the location of these files withing a folder hierarchy
(folder and file names).

SMDBs are provided for a range of flash-carts.  These SMDBs allow
users to dump all of their legally acquired ROMs into a single
folder. When the `build_pack` script is run on that directory, the
ROMs will be analyzed (via hash comparisons) and sorted into complete,
flash-cart friendly Packs, as described in an SMDB. This allows
creators to share file and folder setups without having to share the
ROMs themselves.

## Tools Included

**parse_pack.py** For making SMDBs (example command):
```DOS .bat
"C:\XXX\parse_pack.py" -f "C:\XXX\Folder to be parsed" -o "C:\XXX\SMDB.txt"
```

`-f` (or `--folder`) indicates the target ROM pack

`-o` (or `--output`) is the text file that will contain the hash
values, filenames, and folder structure


**build_pack.py** For building a pack based on a pre-made SMDB (example command):
```DOS .bat
"C:\XXX\build_pack.py" -i "C:\XXX\Folder with unorganized ROMs" -d "C:\XXX\SMDB.txt" -o "C:\XXX\Output folder for rebuilt pack" -m "C:\XXX\Missing.txt"
```

`-i` (or `--input_folder`) is the folder containing the unorganized
ROMs

`-d` (or `--database`) is the SMDB file describing the way your ROMs
are organized

`-o` (or `--output_folder`) is the folder in which to build the ROM
pack

`-m` (or `--missing`) is the text file that will list the ROMs missing
in order to reach the 100% mark

Options for advanced users:

`--file_strategy {copy,hardlink}` changes the way files are copied to
  the destination folder. The default is to physically duplicate the
  files (`copy`). The option `hardlink` avoids file duplication and
  saves storage space for pack builders. Please note that when copying
  to a FAT32 SD card, hardlinks are automatically converted into
  normal files.

`-s` (or `--skip_existing`) avoids overwriting files that already
exist in the destination folder.

Depending on your python installation, you may need to begin your
command with the location of `python.exe` (for example,
`C:\Users\XXX\AppData\Local\Programs\Python\Python36-32\python.exe`). More
information for pack builders in the
[wiki](https://github.com/SmokeMonsterPacks/EverDrive-Packs-Lists-Database/wiki).

## GUI

A graphical user interface is available in
[@Aleyr](https://github.com/Aleyr)'s
[fork](https://github.com/Aleyr/EverDrive-Packs-Lists-Database) for
both the `build_pack.py` and `parse_pack.py` scripts. If you are
having difficulty with the command line options, please consider
trying the GUI version.

## Requirements

[python](https://www.python.org) 3.5 or newer

Linux, MacOS, or Windows

(Linux and MacOS users might need to convert the script and SMDB files
first with the command `dos2unix`)

## Coding

Scripts and code by
[@frederic-mahe](https://github.com/frederic-mahe), with awesome
patches by [@eatnumber1](https://github.com/eatnumber1) and
[@coughlanio](https://github.com/coughlanio).

EverDrive Pack SMDB layouts by
[@SmokeMonsterPacks](https://github.com/SmokeMonsterPacks).

[GUI](https://github.com/Aleyr/EverDrive-Packs-Lists-Database) by [@Aleyr](https://github.com/Aleyr).

## Similar tools

- [clrmamepro](https://mamedev.emulab.it/clrmamepro/),
- [romcenter](http://www.romcenter.com/),
- [romvault](http://www.romvault.com/)
