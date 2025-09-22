this is SFORMAT - a DiskPart++ Command line utility and here's its syntaxes;
languages written in:
C
Assembly
C++
Java
Rust
driver it uses: SFORMAT_HELPER.sys
language resources is gonna be like:
sformat.exe.mui (possibly also .mun)

Windows/Linux/macOS (unix-like systems requires sudo or root to operate but windows either Administrator, SYSTEM or TrustedInstaller.):

erasing:
<NAME_OF_ATA_SECURE_ERASE_COMMAND> <Drive Letter> <\\.\>
example:
SECURITY_ERASE_HDD D:\ | \\.\PhysicalDrive6 (Pipe used foe multiple drives)
(security erase commands may vary!)

initiating/creating/formatting a disk/partition/volume
there are several shortcuts for those subcommands like:
init gpt/mbr \\?\HardDisk3
cr/cre par/vol pri/esp/sp - log/dyn
cre/fot (format) dis gpt/mbr NTFS very quick "Games"
spanned = spd
RAID = ra
simple = sim

spanned:

cre dis1-2-4-5 gpt NTFS very quick "NAS"
simple: same as above but one drive 'dis1'

--------------------

Formatting...

firstly supported filesystems:
ntfs
exfat
btrfs
Oracle ZFS
APFS
FAT
FAT16
ReFS
ZFS
ext1,2,3,4

format types
erase - erases everything with pseudorandom including hidden parts like HPA & HCO
normal - formats with pseudorandom but like normal formatting
very quick - quick format
nuke: finds and issues a SECURITY_ERASE_HDD
fot = format
cre/cr equals fot or gpt/mbr
fot nuke \\.\PhysicalDrive11 - D:\

---------------------

secure shredder

shred/shr

ps = pseudorandom
DoD = 4 overwrite pass department of defense
Gutmann/Gm = 35 overwrite pass
zero/z = what a simple zeroing
<overwrite> - extra/x = overwrites hidden areas (HPA+ HCO)
-p = amount of passes
shr z-ps D:\$Recycle.bin

shr z-ps x C:\Windows\* (deleting windows directory will cause unrecoverable damage, please don't do it)

---------------------

update: Yassin-LLC Update (that's the syntax)

the end... (syntax willl be released either in README or in a .txt for simplicity's sake)
