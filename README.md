# 🛠️ Fix LVM Disk Space Issue on Ubuntu
  
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white) 

When you run `lsblk` and see a large disk (e.g., 3.2TB), but `df -h` shows only a few GB (e.g., 2.7GB), you might be using **LVM** and not utilizing the full disk space.

This guide shows how to extend the logical volume and filesystem to use all available space.

---  
## 🧠 Problem Summary

- `lsblk` shows full disk size:

![img alt](https://github.com/khalidit23/resize-lvm-partition/blob/06d76213fe45d2f51b5f5286b3d6e810ffd90cac/lsblk.png)

- But `df -h` shows:

![img alt](https://github.com/khalidit23/resize-lvm-partition/blob/06d76213fe45d2f51b5f5286b3d6e810ffd90cac/df-h.png)

---
 

## ✅ Solution: Extend LVM Logical Volume and Filesystem

### ️Step 1: Confirm the correct LV name using:

Run:
```bash
lvdisplay
```
### Step 2: Let's extend it to use all the free space using volume group and LV names:
```bash
lvextend -l +100%FREE /dev/datastore/LOG
```
### Step 3: After resizing the logical volume, resize the filesystem:

```bash
resize2fs /dev/mapper/datastore-LOG
```
Now run `df -h` again to check if the disk space has been extended..

## ❤️ Support
If this guide helped you, feel free to star ⭐ this repository and share it with others!
