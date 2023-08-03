# LTO-cheatsheet #

## SCSI tape device names ##

### with auto-rewind ###

  ```/dev/st[0-9]```
  
### without auto-rewind ###

  ```/dev/nst[0-9]```
  
### examples ###

*  ```/dev/st0``` accessing the first tape device with auto-rewind
*  ```/dev/nst1``` accessing the second tape device without auto-rewind

## interacting with the tape using tar ##

### writing to the tape ###

```tar -cvf <tape device name> <path to the data to be written>```

*  -c, --create
    *  Create a new archive.

*  -v, --verbose
    *  Verbosely list files processed.

* -f, --file=*ARCHIVE*
    *   Use archive file or device _ARCHIVE_.
