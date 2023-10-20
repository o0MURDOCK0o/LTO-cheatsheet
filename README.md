# LTO-cheatsheet #

## list SCSI devices with _lsscsi_ ##

```lsscsi``` lists all SCSI devices

## SCSI tape device names ##

### with auto-rewind ###

  ```/dev/st[0-9]```
  
### without auto-rewind ###

  ```/dev/nst[0-9]``` usefull for writing multiple files to tape one by one
  
### examples ###

*  ```/dev/st0``` accessing the first tape device with auto-rewind
*  ```/dev/nst1``` accessing the second tape device without auto-rewind

## interacting with the tape using _tar_ ##

### writing to the tape ###

```tar -cvf <tape device name> <path to the data to be written>```

*  -c, --create
    *  Create a new archive.

*  -v, --verbose
    *  Verbosely list files processed.

* -f, --file=*ARCHIVE*
    *   Use archive file or device _ARCHIVE_.

### list the contents of a tape ###

```tar -tvf <tape device name>```

*  -t, --list
    *  List the contents of an archive.

*  -v, --verbose
    *  Verbosely list files processed.

* -f, --file=*ARCHIVE*
    *   Use archive file or device _ARCHIVE_.

### extract the contents of a tape ###

```tar -xvf <tape device name> -C <path to the data destination>```

*  -x, --extract, --get
    *  Extract files from an archive.

*  -v, --verbose
    *  Verbosely list files processed.

* -f, --file=*ARCHIVE*
    *   Use archive file or device _ARCHIVE_.

*  -C, --directory=*DIR*
    *   Change to _DIR_ before performing any operations.

### examples ###

*   ```tar -cvf /dev/nst0 /tmp```  This command writes all data of the _/tmp_ directory to tape device number 1 without auto-rewinding the tape first
*   ```tar -tvf /dev/st1```  This commond lists the contents of tape device number 2 after auto-rewinding the tape
*   ```tar -xvf /dev/st0 -C /tmp```  This command extracts the contents of tape device number 1 to the _/tmp_ directory after auto-rewinding the tape

## interacting with the tape media changer/library using _mtx_ ##

### inventory the library ###

```mtx -f /dev/sch[0-9] invetory```

* -f _Device_
    *   Use device _Device_.

### print the status of the media changer/library ###

```mtx -f /dev/sch[0-9] status```

### load tape into the tape drive ###

```mtx -f /dev/sch[0-9] load <slotnum> <drivenum>```

### unload the tape from the tape drive into a free slot ###

```mtx -f /dev/sch[0-9] unload <slotnum> <drivenum>```

### examples ###

*  ```mtx -f /dev/sch0 load 4 0``` uses media changer number 1 to load the tape from slot number 4 into drive number 1
*  ```mtx -f /dev/sch2 unload 2 3``` uses media changer number 3 to unload the tape from drive number 4 into slot number 2
