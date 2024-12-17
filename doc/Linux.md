# Tips for Linux

## blkid
```sh
blkid
```
```
/dev/sda2: LABEL="platform" UUID="6a5e2cb5-d099-4a89-ac18-fb0d5b826436" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="platform" PARTUUID="5041fedd-fc5f-45af-8010-b306a54967cd"
/dev/sda1: SEC_TYPE="msdos" LABEL_FATBOOT="efi" LABEL="efi" UUID="E1F3-8619" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="efi" PARTUUID="9c541e81-c17a-4ad5-871a-c46da17a42e7"
```

## diffstat
- 01_before/main.c
  ```c
  #include <stdio.h>
  
  int main() {
      printf("Hello, The World!\n");
  }
  ```
- 02_after/main.c
  ```c
  #include <stdio.h>
  
  int main() {
      printf("Hello, Star Platinum!\n");
  }
  ```
- Run `diff` only.
  ```
  $ diff 01_before/ 02_after/ 
  diff 01_before/main.c 02_after/main.c
  4c4
  <     printf("Hello, The World!\n");
  ---
  >     printf("Hello, Star Platinum!\n");
  ```
- Run `diff` with `diffstat`.
  ```
  $ diff 01_before/ 02_after/ |diffstat 
   main.c |    2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)  
  ```

## fdisk
### Get information from a image file
```sh
fdisk -u -l -o +UUID emlinux-image-weston-emlinux-bookworm-generic-x86-64.wic
```
```
Disk emlinux-image-weston-emlinux-bookworm-generic-x86-64.wic: 1.39 GiB, 1484782592 bytes, 2899966 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 00000000-0000-0000-0000-000065E5E543

Device                                                         Start     End Sectors  Size Type             UUID
emlinux-image-weston-emlinux-bookworm-generic-x86-64.wic   2048  137485  135438 66.1M EFI System       9C541E81-C17A-4AD5-871A-C46DA17A42E7
emlinux-image-weston-emlinux-bookworm-generic-x86-64.wic 139264 2899931 2760668  1.3G Linux filesystem 5041FEDD-FC5F-45AF-8010-B306A54967CD
```

## grep
```sh
grep -r -i foo --include='*.c'
```

## mount
### Mount wic file
```sh
sudo mount -oloop,offset=$(expr 2048 \* 512) emlinux-image-weston-emlinux-bookworm-generic-x86-64.wic /mnt
```
