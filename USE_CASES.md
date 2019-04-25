# Example uses

This file contains some example usages of the stack and tutorial walkthroughs

# Examining a disk image

1. Place disk image in either `./data` or in the isolated files folder using http://droppy.localhost
2. Log in to main forensics workstation
```
docker-compose exec base bash
```
3. Navigate to disk image in either `/data/` or `/isolated-files`
4. Run any of the following suggested tools on the disk image
    * `foremost`
    * `fdisk`
    * `exif-tool`

# Running isolated firefox

Simply connect via VNC to vnc://127.0.0.1:5900

```
open vnc://127.0.0.1:5900
```

The password is `1234`