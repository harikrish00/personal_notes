### Format and mount an external hard drive
- Connect the external hard drive to linux machine
- Once successfully detected by the machine, the log messages shows which device(dev) file.
```
tail -f /var/log/messages -n 25
sdb: sdb1
```
- Create a folder where the harddrive will be mounted
```
mkdir -p /mnt/lacie
```
- Run the following command to format the disk with `vfat` file system so that both Mac and PC can read it
```
mkfs -t vfat -I /dev/sdb1
``` 
- And then mount the newly formatted disk onto the mount folder
```
mount /dev/sdb1 /mnt/lacie/ -o umask=000
```


### Additional Notes:
Mounting HFS drive (this is most probably a disk which is initiated by Macbook and in a HFS Journaled file system)
```
mount -t hfsplus /dev/sda1 /mnt/lacie/
```


### Unmount the hard drive
```
umount -l /mnt/lacie/
umount -f /mnt/lacie/
umount /mnt/lacie/
```