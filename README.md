# RAID-0-IMPLEMENTATION_V2

<br>


<br>




##       Make changes  as  per   screenshorts             





Here is the revised and properly formatted version:

---

# Creating a RAID 0 Setup on Linux  

**RAID 0** provides increased speed by splitting data into smaller parts and writing them to multiple drives simultaneously. However, it does not offer redundancy, so if one disk fails, all data will be lost. Below are the steps to create a RAID 0 array on Linux.  

## Pre-requisites:  
- A Linux system (Ubuntu, CentOS, etc.)  
- At least two unformatted disks (e.g., `/dev/sdb`, `/dev/sdc`).  
- A root or sudo user to execute commands.  

---

## Steps to Create a RAID 0 Array  

### 1. Install `mdadm` (RAID Management Tool):  
`mdadm` is the utility used to manage RAID arrays on Linux. Install it using the following commands:  

**On Ubuntu/Debian:**  
```bash
sudo apt update  
sudo apt install mdadm  
```  

**On CentOS/RHEL:**  
```bash
sudo yum install mdadm  
```  

---

### 2. Prepare the Disks:  
Ensure the disks are unformatted. List the available disks using:  
```bash
sudo lsblk  
```  

Identify the disks you want to use for the RAID array (e.g., `/dev/sdb` and `/dev/sdc`).  

---

### 3. Create the RAID 0 Array:  
Use `mdadm` to create the RAID 0 array. For example, to create an array named `/dev/md0` with two disks `/dev/sdb` and `/dev/sdc`, run:  
```bash
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb /dev/sdc  
```  

**Explanation of Options:**  
- `--create /dev/md0`: Creates the RAID array and names it `/dev/md0`.  
- `--level=0`: Specifies RAID 0.  
- `--raid-devices=2`: Defines the number of devices (disks) in the array.  

Verify the RAID array creation:  
```bash
sudo mdadm --detail /dev/md0  
```  

---

### 4. Check RAID Array Status:  
Monitor the status of the RAID array creation using:  
```bash
cat /proc/mdstat  
```  

This displays the status of all RAID arrays and indicates whether they are synchronizing.  

---

### 5. Create a Filesystem on the RAID Array:  
Format the RAID array with a filesystem. For example, to create an ext4 filesystem:  
```bash
sudo mkfs.ext4 /dev/md0  
```  

Verify the filesystem creation:  
```bash
sudo blkid /dev/md0  
```  

---

### 6. Mount the RAID Array:  
To use the RAID array, mount it:  

1. Create a mount point:  
   ```bash
   sudo mkdir /mnt/my_raid0  
   ```  

2. Mount the RAID array:  
   ```bash
   sudo mount /dev/md0 /mnt/my_raid0  
   ```  

Verify the mount:  
```bash
df -h  
```  

Alternatively:  
```bash
mount | grep /mnt/my_raid0  
```  

---

### 7. Make the Mount Persistent:  
To ensure the RAID array mounts automatically after a reboot, edit the `/etc/fstab` file:  
```bash
sudo nano /etc/fstab  
```  

Add this line:  
```
/dev/md0  /mnt/my_raid0  ext4  defaults  0  0  
```  

Verify the `fstab` entry:  
```bash
cat /etc/fstab  
```  

---

### 8. (Optional) Monitor the RAID Array:  
Periodically check the health and status of the RAID array:  
```bash
sudo mdadm --detail /dev/md0  
```  

This provides detailed information about the RAID array, such as its status, devices, and RAID level.  

--- 

By following these steps, you can successfully set up a RAID 0 array on your Linux system. Ensure you have backups of important data since RAID 0 does not provide redundancy.  
































<br>


<br>





















<br>


![1](https://github.com/user-attachments/assets/22f5611f-477e-44a8-b0e2-fb719c957c63)

<br>







<br>



![2](https://github.com/user-attachments/assets/2422f2c2-69e3-44ee-a0a3-43bffdd0f896)

<br>







<br>



![3](https://github.com/user-attachments/assets/3d67f5c5-1d53-4d55-ace9-362827c77572)


<br>







<br>




![4](https://github.com/user-attachments/assets/1d455bd2-41d7-4051-b184-86d837261b1c)


<br>





<br>





![5](https://github.com/user-attachments/assets/fe45e993-0375-4603-9cf8-6a3dd0ff2c6e)






<br>




<br>


![6](https://github.com/user-attachments/assets/5aac779e-328d-4e7a-8bcd-f2356c92d80d)






<br>




<br>



![7](https://github.com/user-attachments/assets/18288c74-2c60-404d-b2ee-c7f717662267)



<br>
<br>



