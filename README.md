## PBRVIEW.G4B v0.5 (20260111), by deomsh
<pre><code>Function: Function: display FAT12/16, FAT32, NTFS or exFAT Partition Boot Record
PBRVIEW.G4B [OPTIONAL] DEVICE|DISK|FILE [/MS|/PQ|/J|/BLUE]
OPTIONAL: --BPB=FS --start=N|--skip=n|--force=N N/n: Start Sector/byte (0-N/n)
 If DEVICE is not a Partition use Image-file, Disk (watch CD/DVD!) or Blocklist
Optional: '/M[S]|/P[Q]|/J[L]' for Microsoft, PowerQuest or Jaclaz names/ colors
          '/B[LUE]' changes default names/ colors to blue color
Remarks: 
If FILE contains spaces/= use escaped chars '\ '/  '\=' or double qoutes around
With --start=N|--force=N Sector number is in 512 byte units
 With --start=N|--skip=n|--force=N Filesystem derived from Jump-code only
 First 16MB is searched for EBxx90/ E9xxxx (0x8000 sectors in 512 byte Sectors)
 Without valid Media Descriptor found, search is continued/ skipped
With --BPB=FS => FS forces File System: most useful if FS is set to FAT
In case of exFAT: switch /M[S], /P[Q] or /J[L] changes colors only
Unlock line 31 to change default colors to blue
Text mode of Grub4dos for Uefi NOT supported, use some Graphics mode
Example: PBRVIEW.G4B (hd0,0)
Example: PBRVIEW.G4B (fd0) /MS
Example: PBRVIEW.G4B --start=63 (hd0) /J
Example: PBRVIEW.G4B (hd0,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --force=2079 "(hd1,0)/Fat Image on Logical Partition.IMG"
Example: PBRVIEW.G4B --skip=0x7E00 (0xe0)0+0x800 /BLUE
Example: PBRVIEW.G4B --BPB=FAT (hd1,0) /PQ</code></pre> 

### History
v0.5  
New: uuid & label set to N/A if ebpb signature = 0x28  
New: option --BPB=FS to force FAT below Version 4.0  
Bugfix: better detection of graphicsmode 800x600 and above, for output FAT32-table in one screen (VMWare)  

v0.4.1  
Help: adjusted for "FILE" and new switch  
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
![PBRVIEW G4B v0 5 version and textstat](https://github.com/user-attachments/assets/138284f3-a946-41f8-95a3-5b78308bda3a)

#### Smallhelp
![PBRVIEW G4B v0 5 Smallhelp](https://github.com/user-attachments/assets/d846f4f0-91c5-4dcd-963e-b7643a3ee4bd)

#### Help
![PBRVIEW G4B v0 5 Help](https://github.com/user-attachments/assets/59dd4616-109f-4140-a56a-1f74667b4c31)

#### PBRVIEW.G4B (fd0) (Floppy 3840KB, FAT12, Default names/ colors, with notes)
![PBRVIEW G4B v0 4 1 on (fd0) Floppy 3840KB, FAT12](https://github.com/user-attachments/assets/85931097-cc55-4761-8d50-8ec31643b880)

#### PBRVIEW.G4B --start=63 (hd2) /J (Hard Disk Partition 2GB, FAT16, Jaclaz' names/ colors)
![PBRVIEW G4B v0 4 1 --start=63 (hd2) -J HDD 2GB, FAT16](https://github.com/user-attachments/assets/1ec87d9c-0e1e-4ca0-8e21-18a24d7b8e4c)

#### PBRVIEW.G4B (hd3) /MS (Hard Disk Partition 60MB, NTFS on Sector 128 - auto-searched, Microsoft' names/ color)
![PBRVIEW G4B v0 4 1 (hd3) -MS HDD 64MB, auto-searched NTFS](https://github.com/user-attachments/assets/d91c0bf7-90e6-4f6c-80a2-78d629355f64)

#### PBRVIEW.G4B (hd4) /BLUE (Hard Disk Partition 55MB, exFAT on sector 2048 - auto-searched, Blue colors, no notes on exFAT available)
![PBRVIEW G4B v0 4 1 (hd4) -BLUE HDD 64MB, auto-searched exFAT on sector 2048](https://github.com/user-attachments/assets/136bc1f9-550f-4402-9f02-e3282df5b6f3)

#### PBRVIEW.G4B --force=2079 "(hd1,0)/Fat Image on Logical Partition.IMG" (Logical Partition on Hard Disk Image 512MB, FAT16 on Sector 2079, Default names/ colors, with notes)
![PBRVIEW G4B v0 4 1 --force=2079 ''(hd1,0)-Fat Image on Logical Partition IMG'' Logical HDD image 512MB, FAT16](https://github.com/user-attachments/assets/ba4b31ce-84b5-4d83-82ab-0ed551291d30)

#### PBRVIEW.G4B --skip=0x7E00 (hd1) (Hard Disk Partition 16GB, FAT32 on offset 0x7E00, Default names/ colors, with notes, in Grub4dos' Text mode)
![PBRVIEW G4B v0 4 1 --skip=0x7E00 (hd1) HDD 16GB, FAT32 screen I](https://github.com/user-attachments/assets/e352573a-84dd-4007-b8ff-f5add592ac31)
![PBRVIEW G4B v0 4 1 --skip=0x7E00 (hd1) HDD 16GB, FAT32 screen II](https://github.com/user-attachments/assets/22b7d609-c2c3-4e97-b971-9bd6d891cc4f)

#### Same as above, but in grub4dos' graphicsmode -1 800
![PBRVIEW G4B v0 4 1 --skip=0x7E00 (hd1) HDD 16GB, FAT32 in one screen with graphicsmode -1 800](https://github.com/user-attachments/assets/f1cdf2d2-bb87-41df-8f67-5884ede5bc69)

#### PBRVIEW.G4B --start=6 (hd0,0) /PQ (Hard Disk Partition 16GB, FAT32 Backup of Bootsector on Sector 6, Powerquest' names/ colors, in Grub4dos' graphicsmode -1 800)
![PBRVIEW G4B v0 4 1 --start=6 (hd0,0) -PQ HDD 16GB, FAT32 backup bootsector Powerquest Names- Colors](https://github.com/user-attachments/assets/cb6e5484-5fd1-4636-9bfb-a966abc14a70)

#### PBRVIEW.G4B (0xe0)3775+10000 (El Torito 1440k Boot Floppy NOT at CD Sector-border, but with - relative - offset=0x600, auto-searched, Default names/ colors, with notes)
![PBRVIEW G4B v0 4 1 (0xe0)3775+10000 El Torito 1440k bootfloppy NOT at cd-sector border but offset=0x600, auto-searched](https://github.com/user-attachments/assets/ba485554-acf5-46af-a992-79989253c992)

#### PBRVIEW --BPB=FAT (hd1,0) (MS-DOS 3.00 Boot Parameter Block: watch use of High word in Hidden Sectors for Drive Number)
![PBRVIEW G4B v0 5 view of MS-DOS 3 00 BPB with option --BPB=FAT on (hd1,0)  WATCH high word if Hidden Sectors!](https://github.com/user-attachments/assets/186e39d3-7ba1-4dd1-aa63-6b7cc2f4c713)

#### PBRVIEW --BPB=FAT (hd1,0) (MKFATIMG.G4B' MSDOS20 Boot Parameter Block: watch insertion of 'FAT' in Boot Code to trick Grubutil fat)
![PBRVIEW G4B v0 5 view of MS-DOS 2 00 BPB with option --BPB=FAT on (hd1,0)  WATCH File System to trick Grubutil &#39;fat&#39;](https://github.com/user-attachments/assets/31ef5c36-fca5-4401-b511-accea66c140d)

#### Better compatibility with VMWare graphicsmodes: output of FAT32-table in one screen with resolution 800x600
![PBRVIEW G4B v0 5 view of USB64GB FAT32 on 800x600 in VMWare](https://github.com/user-attachments/assets/ac949148-4f6d-492e-92f3-b57e48de6fde)
