PBRVIEW.G4B v0.2 (20231102), by deomsh
Function: Function: display FAT12/16, FAT32, NTFS or exFAT Partition Boot Record
PBRVIEW.G4B [--start=N|--skip=n|--force=N] DISK|DEVICE|FILE [/MS|/PQ|/JL]
Optional: --start=N|--skip=n|--force=N: N/n is starting sector/byte (0-N/n)
 If no partition is given use image-file, disk or blocklist
Optional: /MS|/PQ|/JL for Microsoft, PowerQuest or Jaclaz names
Remarks: 
FILE can be a blocklist too
With --start/--force N sector number is in 512 byte units
 With --start/--skip/--force filesystem derived from jump-code only
 First 4MB is searched for EBxx90 (0x2000 sectors in 512 byte sectors)
In case of exFAT: switch /MS, /PQ or /JL changes colors only
Unlock line 29 to change default colors to blue
Text mode of grub4efi not supported, use some graphics mode
Example: PBRVIEW.G4B (hd0,0)
Example: PBRVIEW.G4B (fd0) /MS
Example: PBRVIEW.G4B (rd) /PQ
Example: PBRVIEW.G4B (hd0) /JL
Example: PBRVIEW.G4B --start=63 (hd0)
Example: PBRVIEW.G4B (hd0,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --force=1008 (hd1,0)/ISOFILE.ISO
Example: PBRVIEW.G4B --skip=0x3F0 (hd1,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --skip=0x7E00 (cd)0+0x800
Example: PBRVIEW.G4B (0xe0)0x567+1

History
Version 0.2
Bug fixes
Added switch with 'Good names' of Jaclaz/ Wonko the Sane
Update of exFAT names
Added notes in Default view (except exFAT)
Exit in case of grub4efi text mode

Version 0.1
First published version
