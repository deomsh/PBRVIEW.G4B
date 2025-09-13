## PBRVIEW.G4B v0.4.1 (20250913), by deomsh
<pre><code>Function: Function: display FAT12/16, FAT32, NTFS or exFAT Partition Boot Record
PBRVIEW.G4B [--start=N|--skip=n|--force=N] DISK|DEVICE|FILE [/MS|/PQ|/JL|/BLUE]
Optional: --start=N|--skip=n|--force=N: N/n is starting Sector/ Byte (0-N/n)
 If DEVICE is not a Partition use Image-file, Disk (watch CD/DVD!) or Blocklist
Optional: '/M[S]|/P[Q]|/J[L]' for Microsoft, PowerQuest or Jaclaz names/ colors
          '/B[LUE]' changes default names/ colors to blue color
Remarks: 
If FILE contains spaces/= use escaped chars '\ '/  '\=' or double qoutes around
With --start=N|--force=N Sector number is in 512 byte units
 With --start=N|--skip=n|--force=N Filesystem derived from Jump-code only
 First 16MB is searched for EBxx90/ E9xxxx (0x8000 sectors in 512 byte Sectors)
 Without valid Media Descriptor found, search is continued/ skipped
In case of exFAT: switch /M[S], /P[Q] or /J[L] changes colors only
Unlock line 31 to change default colors to blue
Text mode of Grub4dos for Uefi NOT supported, use some Graphics mode
Example: PBRVIEW.G4B (hd0,0)
Example: PBRVIEW.G4B (fd0) /MS
Example: PBRVIEW.G4B (rd) /PQ
Example: PBRVIEW.G4B --start=63 (hd0) /J
Example: PBRVIEW.G4B (hd0,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --force=2079 "(hd1,0)/Fat Image on Logical Partition.IMG"
Example: PBRVIEW.G4B --start=6 (hd0,0) /BLUE
Example: PBRVIEW.G4B --skip=0x7E00 (0xe0)0+0x800</code></pre> 

### History
v0.4.1  
Adjusted: Help for "FILE" and new switch  
New: switch /BLUE to change default colors  
Better: Early exit if target-Device/ Disk does not exist  
Adjusted: notes color with 'BLUE'  
Bugfix: freezes with --force=n if no PBR found  

v0.4  
NEW: FILE can be used between double-quotes if containing spaces or '='  

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

### Screenshots

