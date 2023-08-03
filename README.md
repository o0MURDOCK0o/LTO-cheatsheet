# LTO-cheatsheet #

## SCSI tape device names ##

### with auto-rewind ###
  ```/dev/st[0-9]```
### without auto-rewind ###
  ```/dev/nst[0-9]```
### examples ###

*  ```/dev/st0``` accessing the first tape device with auto-rewind
*  ```/dev/nst1``` accessing the second tape device without auto-rewind
