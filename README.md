# LTO-cheatsheet #

## SCSI tape device names ##

### with auto-rewind ###

  ```/dev/st[0-9]```
  
### without auto-rewind ###

  ```/dev/nst[0-9]```
  
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
