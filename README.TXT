PBRVIEW.G4B v0.3 (20240728), by deomsh
Function: Function: display FAT12/16, FAT32, NTFS or exFAT Partition Boot Record
PBRVIEW.G4B [--start=N|--skip=n|--force=N] DISK|DEVICE|FILE [/MS|/PQ|/JL]
Optional: --start=N|--skip=n|--force=N: N/n is starting sector/byte (0-N/n)
 If DEVICE is not a partition use image-file, disk or blocklist
Optional: '/M[S]|/P[Q]|/J[L]' for Microsoft, PowerQuest or Jaclaz names
Remarks: 
FILE can be a blocklist too; CD/DVD: blocklist only
With --start/--force N sector number is in 512 byte units
 With --start/--skip/--force filesystem derived from jump-code only
 First 16MB is searched for EBxx90/ E9xxxx (0x8000 sectors in 512 byte sectors)
 Without valid Media Descriptor found, search is continued/ skipped
In case of exFAT: switch /M[S], /P[Q] or /J[L] changes colors only
Unlock line 31 to change default colors to blue
Text mode of grub4efi not supported, use some graphics mode
Example: PBRVIEW.G4B (hd0,0)
Example: PBRVIEW.G4B (fd0) /MS
Example: PBRVIEW.G4B (rd) /PQ
Example: PBRVIEW.G4B (hd0) /JL
Example: PBRVIEW.G4B --start=63 (hd0)
Example: PBRVIEW.G4B (hd0,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --force=1008 (hd1,0)/ISOFILE.ISO
Example: PBRVIEW.G4B --start=6 (hd0,0) /M
Example: PBRVIEW.G4B --skip=0x7E00 (0xa0)0+0x800

History
v0.3
New: abbreviation of switches possible
New: better detection of exFAT & NTFS
New: echo with --force if no PBR found + bytepsec=2k with CD-ROM
Max search area now 16MB
New: search includes finding E9xxxx
Better comment for hidden sectors
New: CD-ROM starts at 0x9f; still acces to harddrive (hd31)
HELP: small changes
Bugfix: bad read of jump & bootsignature if zeros!
New: ISO's always treated as CD-ROM
New: improved --force count with CD-ROM
New: --start compatible with CD-ROM including search
New: skip/ search again with empty OEM
New: Full FAT32 showed in ONE screen with graphicsmode > 640 (from 800x600 onwards)
Version 0.2.1
Bugfix: correct display of File-system for FAT12 bootsectors >=32MB
Version 0.2
Bug fixes
Added switch with 'Good names' of Jaclaz/ Wonko the Sane
Update of exFAT names
Added notes in Default view (except exFAT)
Exit in case of grub4efi text mode
Added negative values on NTFS: BPB_ClusPerMft & BPB_ClusPerIndx
Calculation of byte-values if negative values on NTFS in '/JL' & Default view (+ switch name)

Version 0.1
First published version
