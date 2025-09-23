# SFORMAT
SFORMAT is a powerful and portable command-line utility for managing disks, partitions, and volumes across multiple platforms. Designed for advanced users, it supports secure erasing, formatting, shredding, verifying drive integrity, and more.

The tool is provided as a **portable executable** in `.7z` and `.zip` formats. No installation is required—simply extract and use. [The tool is still portable (I like it that way), use it anywhere, even live USBs & WinPE/RE];
The tool can read .txt, .cmd, or .bat & execute them.

---

## Installation
SFORMAT is available as a portable tool, distributed in `.7z` and `.zip` formats. Simply extract the archive's contents and run the executable from your terminal.

### Download
- [Download the latest version (7z)](Https://Github.com/Yassin-LLC/SFormat/Releases)
- [Download the latest version (zip)](Https://Github.com/Yassin-LLC/SFormat/Releases)

---

## Supported Programming Languages
The program leverages multiple programming languages for its development:
- C
- Assembly
- C++
- Java
- Rust

### Driver Used
- `SFORMAT_HELPER.sys`

### Language Resources
- `sformat.exe.mui` (possibly also `.mun`)

---

## Supported Operating Systems
SFORMAT is compatible with the following operating systems:
- **Windows:** Requires Administrator, SYSTEM, or TrustedInstaller privileges.
- **Linux/macOS:** Requires `sudo` or root privileges.

---

## Commands and Syntax
SFORMAT comes with a wide range of commands for managing disks and partitions. Below is a detailed breakdown of each command and its syntax.

---

### 1. Erasing
Securely erase disks or partitions using ATA commands.

#### Syntax:
```
<NAME_OF_ATA_SECURE_ERASE_COMMAND> <Drive Letter> <\\.\>
```

#### Example:
```
SECURITY_ERASE_HDD D:\ | \\.\PhysicalDrive6
```
> Note: Pipe (`|`) can be used for multiple drives. Security erase commands may vary!

---

### 2. Initiating/Creating/Formatting a Disk, Partition, or Volume
Use these commands to initialize, create, or format disks, partitions, or volumes.

#### Shortcuts for Subcommands:
- `init gpt/mbr \\?\HardDisk3`
- `cr/cre par/vol pri/esp/sp - log/dyn`
- `cre/fot (format) dis gpt/mbr NTFS very quick "Games"`

#### Abbreviations:
- Spanned = `spd`
- RAID = `ra`
- Simple = `sim`

#### Examples:
- **Spanned Volume:**
  ```
  cre dis1-2-4-5 gpt NTFS very quick "NAS"
  ```
- **Simple Volume:**
  ```
  cre dis1 gpt NTFS very quick "Games"
  ```

---

### 3. Formatting
SFORMAT supports a wide range of filesystems and formatting options.

#### Supported Filesystems:
- NTFS
- exFAT
- Btrfs
- Oracle ZFS
- APFS
- FAT, FAT16
- ReFS
- ZFS
- ext1, ext2, ext3, ext4

#### Format Types:
- `erase`: Erases everything with pseudorandom data, including hidden parts (HPA & HCO).
- `normal`: Formats with pseudorandom data (like normal formatting).
- `very quick`: Quick format.
- `nuke`: Finds and issues a `SECURITY_ERASE_HDD` command.

#### Example:
```
fot nuke \\.\PhysicalDrive11 - D:\
```

---

### 4. Secure Shredder
SFORMAT includes functionality for securely shredding files and directories.

#### Syntax:
```
shred/shr <method> <options> <target>
```

#### Methods:
- `ps`: Pseudorandom data.
- `DoD`: 4 overwrite passes (Department of Defense standard).
- `Gutmann/Gm`: 35 overwrite passes.
- `zero/z`: Zeroing (writes zeros).
- `|`: Used for multiple objects.

#### Options:
- `<overwrite>`: `extra/x` (overwrites hidden areas like HPA & HCO).
- `-p`: Number of passes.

#### Examples:
- Shred the recycle bin:
  ```
  shr z-ps D:\$Recycle.bin
  ```
- Shred system files (Warning: May cause irrecoverable damage):
  ```
  shr z-ps x C:\Windows\*
  shr z-DoD \DosDevices\:=disk0
  ```

---

### 5. Checking Fraudulent Drives
Fraudulent drives are storage devices that have been tampered with or misrepresented (e.g., fake storage capacity). The `markdsk` command helps verify and validate such drives.

#### Syntax:
```
markdsk <DriveLowLevelName> <Level>
```

#### Levels:
- `Kid`: Tests 43 areas.
- `Deep`: Tests 256 areas.
- `Validrive`: Tests 576 areas.
- `Forensic`: Tests 1024 areas.
- `WantItExtreme`: Tests 10983 areas.

#### Example:
```
markdsk \\.\PhysicalDrive2 Forensic
```
> Writes to 1024 areas across the disk to verify its integrity.

---

### 6. Force-Kill Processes
The `-force` and `--force` options allow you to terminate any related processes using the kernel driver. These options are particularly useful when operations are blocked by active processes.

#### Syntax:
```
<command> -force
<command> --force
```

#### Details:
- `-force`: Kills any related processes.
- `--force`: Uses the kernel driver to kill/end any related processes (since drivers operate close to the kernel).

#### Notes:
- These options can be used as the first or last argument.
- The tool is powerful by default, but if it fails, these options may help.

#### Example:
```
sformat --force <command>
```

---

### 7. Update
The `Yassin-LLC Update` command checks for updates to the tool.

#### Syntax:
```
Yassin-LLC Update
```

---

## Notes
- Syntax examples are also provided in a `.txt` file for simplicity.
- The tool is extremely powerful and should be used with caution.

---

### Important Note for Super-Advanced & Novice Users!

- **WARNING:** Using the tool on the wrong drives will cause **unstoppable** and **unrecoverable** damage!  
  The owner is **NOT** responsible for any misuse or resulting damage. The tool is extremely powerful. Use it wisely.

---

## License
This tool is provided under the [MIT License](https://mit-license.org/).
