PBRVIEW.G4B v0.1 (20231015), by deomsh
Function: display Partition Boot Record on FAT, NTFS or exFAT
PBRVIEW.G4B [--start=N|--skip=n|--force=N] DISK|DEVICE|FILE [/MS|/PQ]
Optional: --start=N|--skip=n|--force=N: N/n is starting sector/byte (0-N/n)
 Use if no partition is given: image-file, disk or blocklist
Optional: /MS|/PQ for Microsoft or PowerQuest style
Remarks: 
FILE can be a blocklist too
With --start/--force N sector number is in 512 byte units
 With --start/--skip/--force filesystem derived from jump-code only
 First 4MB is searched for EBxx90 (0x2000 512 byte sectors)
In case of exFAT switch /MS or /PQ changes colors only
Example: PBRVIEW.G4B (hd0,0)
Example: PBRVIEW.G4B (fd0) /ms
Example: PBRVIEW.G4B (rd) /pq
Example: PBRVIEW.G4B --start=63 (hd0)
Example: PBRVIEW.G4B (hd0,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --start=1008 (hd1,0)/IMAGE.IMG
Example: PBRVIEW.G4B --force=1008 (hd1,0)/ISOFILE.ISO
Example: PBRVIEW.G4B --skip=0x3F0 (hd1,0)/FATIMAGE.IMG
Example: PBRVIEW.G4B --start=6 (hd0,0) /ms
Example: PBRVIEW.G4B --skip=0x7E00 (cd)0+0x800
Example: PBRVIEW.G4B (0xe0)0x567+1

History
Version 0.1
First published version
