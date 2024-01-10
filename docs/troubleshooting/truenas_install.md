When installing TrueNAS Cobia under Proxmox, the following error occurs error:
```
lsblk: CANT_FIND_sda1_OR_sdap1: nor a block device
```

This happens because the install changes partitions and the OS is slow to react to the changes.

## Fix

Edit file `/usr/sbin/truenas-install`, search for `lsblk`. The search brings you to a function called `get_media_description()` where the offending lsblk is.  Find the comment `# need to settle so that lsblk output is stable` and place `sleep 20` there.