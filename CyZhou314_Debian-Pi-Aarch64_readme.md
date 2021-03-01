![openfans](/images/openfans.png)&nbsp;&nbsp;&nbsp;&nbsp;![amatfan.png](/images/amatfan.png)、

# =★= Debian-Pi-Aarch64 =★=

*The newest Raspberry Pi 64-bit OS 2.0 Release!!!*

*This is the first 64-bit system in the world to support all Raspberry Pi 64-bit hardware!!! (Include: 2Bv1.2, 3B, 3B+, 3A+, 4B)*

![catalina](./images/catalina.jpg)

```
There are always someone who do everything possible to find other's trouble, 
in order to avoid misleading,
We will explain all the help and reference that we have used and applied. 
If there are any omissions, please feel free to give us feedback in time.
Thanks again to all those who have helped us.
```

## Official Documentation Version 2.0

***[中文版(Chinese)](README_zh.md)***

***English edition translation is continuously optimized and adjusted ...***

Give me a star, just a click, I will be very happy and satisfied...  :)

**Gitee Repo:** [gitee.com/openfans-community/Debian-Pi-Aarch64](https://gitee.com/openfans-community/Debian-Pi-Aarch64)

**Github Repo:** [github.com/openfans-community-offical/Debian-Pi-Aarch64](https://github.com/openfans-community-offical/Debian-Pi-Aarch64)

----

The newest **Raspberry Pi 64-bit OS**, **OPENFANS** open source community & Raspberry **Pi Fan** base community Co-Produced.

This is an **official version** readme for the newest version 2.0 of 64-bit OS which is support for the **full range** of 64-bit CPU Raspberry Pi such as **3B, 3B+, 3A+, 4B**.

**The passed system version: 1.0 and 2.0 preview has been without any updates or supported.**

The **"Old Readme"** was viewed **[here](./README_ORGI.md).** ( - Just A Chinese Edition)

**First, Please read this document carefully before your questions, maybe your answers have included in this document (We'll refuse to reply any answered questions).**

**Attention, please! Besides this document, any other documents in this Git repository are no longer supported (Except linked file form this document), just for a developer's archive.**

## Attention!

- All commands executed of this article, unless specified, are executed under the **root** privileges by default!!

- With any problems, be sure to upgrade your **system**, **firmware** and **kernel** to the **latest** version first. Click **[here](./README.md#5-update-and-upgrade)** to check the **latest version** and learned how to upgrade your **system**, **kernel** and **firmware**.

## Notice:

The latest version of the system: **2020-06-22-v2020-2.0-U4-Release** 

If you had found a *Chromium browser interface display error* issue on version **202006 U3** please see [here](./README.md#3-163-chromium-browser-interface-display-error).  **This issue had fixed after version >=20200617U3**

```
The latest version of kernel and firmware:
2020-06-22-v2020-2.0-U4-Release (recommended update)
```

*The system version "2020-06-22-v2020-2.0-U4-Release" don't need upgrade the kernel and firmware to "2020-06-22-2.0-U4"*

***Note:*** **Fimware >=U3, >=U4 do not support upgrade from version  >/etc/apt/sources.list ; \
sudo dpkg --add-architecture armhf ; sudo apt update ; \
cd ~ ; wget https://www.realvnc.com/download/file/vnc.files/$vnc_pkg ; \
sudo apt install ./$vnc_pkg ; \
rm -rf ./$vnc_pkg ; \
sudo dpkg --remove-architecture armhf ; sudo apt update ; \
sudo systemctl enable vncserver-x11-serviced.service ; \
sudo systemctl start vncserver-x11-serviced.service ; \
sudo \
sed -i '/deb http:\/\/mirrors.tuna.tsinghua.edu.cn\/debian\/ sid main non-free contrib/d' \
/etc/apt/sources.list ; \
sudo apt clean all ; sudo apt update
```

**Attention please!!**

```
sudo \
sed -i '/deb http:\/\/mirrors.tuna.tsinghua.edu.cn\/debian\/ sid main non-free contrib/d' \
/etc/apt/sources.list ; \
```

**Don't miss this command in the process of installing RealVNC on it above!!!**

Click [here](https://www.realvnc.com/en/connect/download/viewer/) to download RealVNC client

Install and run the client, enter the IP address directly, do not need to fill in the port, username, and password is your system's login user and password.

**PS:**

*Some advanced instructions for Realvnc:*

#### Installed system unit for VNC Server in Service Mode Mode Daemon

Start or stop service with:

```
systemctl (start-stop) vncserver-x11-service.service
```

Mark or unmark the service to be started at boot time with:

```
systemctl (enable-disable) vncserver-x11-service.service
```

How to kill all Process:

```
killall vncserver-x11-core vncserver-x11 vncagent vncserverui
```

**When you do not have a monitor you need do this way**

*VNC Server Virtual Mode*

In this mode, the VNC connect address is:

```
your-Rpi-ip-address:1
```

```
## Mode A:

Installed system unit for VNC Server in Virtual Mode Daemon
(This feature needs a RealVNC license)

Start or stop service with:

    systemctl (start-stop) vncserver-virtuald.service

Mark or unmark the service to be started at boot time with:

    systemctl (enable-disable) vncserver-virtuald.service
```

```
## Mode B:

Another way run Virtual Mode Daemon:
(Custom way without license)
(From Pi forum https://www.raspberrypi.org/forums/viewtopic.php?t=249124)

Do as the follow steps:

1. Install a package: 

    apt install xserver-xorg-video-dummy -y

2. Run command:

    killall vncserver-x11-core vncserver-x11 vncagent vncserverui ;\
    systemctl stop vncserver-x11-serviced.service ;\
    systemctl disable vncserver-x11-serviced.service ;\
    systemctl stop vncserver-virtuald.service ;\
    systemctl disable vncserver-virtuald.service

3. Create a service script: 

/usr/lib/systemd/system/vncserver-pi.service

---------------------------------------------------
[Unit]
Description=VNC Server in Virtual Mode daemon
After=network.target

[Service]
User=pi
Type=forking
ExecStart=/usr/bin/vncserver :1
ExecStop=/usr/bin/vncserver -kill :1
Restart=on-failure
RestartSec=5
KillMode=process

[Install]
WantedBy=multi-user.target
---------------------------------------------------

4. To enable the system Xorg server for all users, run:

    vncinitconfig -enable-system-xorg

    All answers need to choose "Y"

    If you wanna disable, run:

    vncinitconfig -disable-system-xorg

5. Generate a "/etc/X11/vncserver-virtual.conf" conf file, run:

    vncinitconfig -virtual-xorg-conf

6. Then enable and start service:

    systemctl enable vncserver-pi.service
    systemctl start vncserver-pi.service


Known issue:
This mode isn't support restart vncserver-pi.service
You need to reboot system.
```

### 3-11. Switch Sound Output Channels

Vesrion 2.0: System Default Use the **HDMI** to output audio.

The commands for switching the sound output:

```
amixer cset numid=3 2

## Set the output here to 2, which is HDMI.
## Setting the output to 1 switch to the analog signal (that is, the headphone connector).
## The default setting is 0, which represents automatic selection.
```

After you have finished modifying your audio settings, you need to restart your Raspberry Pi in order for your changes to take effect.

**If you're still not getting sound via HDMI:**

In some rare cases, it is necessary to edit config.txt to force HDMI mode (as opposed to DVI mode, which does not send sound). 

You can do this by editing **/boot/config.txt** and setting **hdmi_drive=2** , then rebooting for the change to take effect.


### 3-12. 32-Bit Software Armhf Support

```
dpkg --add-architecture armhf
apt update

## The 32-bit "libc6:armhf" base library needs to be installed first
apt install libc6:armhf

apt install [Other package name]:[armhf]

## Install 32-bit software Please add suffix ":armhf" after the name of the package
```

### 3-13. Enabled And Start Docker Service

The **BaseOS** and **Desktop Full-Features Versions** are not enabled by default and require manual start-up.

```
## Turn on the Docker service automatically start
systemctl enable docker.service

## Start Docker service
systemctl start docker.service

######

## Stop Docker services
systemctl stop docker.service

## Disable Docker service from booting
systemctl disable docker.service
```

### 3-14 Enabled And Start CecOS CaaS Container Cloud

The **BaseOS** and **Desktop Full-Features Versions** are not enabled by default and require manual start-up.

**Note: To enable the CecOS CaaS container cloud service, you must enable and start the docker service first!**

```
## Turn on the CecOS CaaS Container Cloud service automatically start
systemctl enable cecos-caas.service

## Start CecOS CaaS Container Cloud service
systemctl start cecos-caas.service

######

## Stop CecOS CaaS Container Cloud service
systemctl stop cecos-caas.service

## Disable CecOS CaaS Container Cloud service from booting
systemctl disable cecos-caas.service
```

### 3-15 Create And Joined Or Exit And Left A Docker Cluster

```
## Initialize and join a Docker Swarm Cluster
docker swarm init

## View cluster node status
docker node ls

## exit Docker Swarm Cluster
docker swarm leave -force
```

### 3-16. FAQ NOTE

#### 3-16.1 Using Profiles To Connect To The Wireless Networks Of Graphical Desktop Environment

The graphical desktop environment uses a profile to connect to a wireless network, and after modifying the ** /boot/wpa_supplicant.conf** file, to ensure good network compatibility, do the following:

with root user identity:

```Shell
systemctl network Manager
```

Then execute:

```Shell
sed -i  \
's/sudo systemctl restart NetworkManager/## sudo systemctl restart NetworkManager/g' \
/home/pi/.xsessionrc
```

Finally, after restart all done.

#### 3-16.2 Version mismatch when installing packages using APT command

**Problem Description:**

When using the command apt to install the deb package online, you may encounter the problem that a matching version cannot be found, such as:

```
The following packages have unmet dependencies:
 package-name-1 : Depends: package-name-2 ( >= x.x.x-xxx-2 ) but x.x.x-xxx-1 is to be installed
              Recommends: package-name-3 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

**Reason:**

This is because some of the newer upstream packages installed on our system do not match the version of the packages in the default repository.

**Solution:**

To temporarily enable the upstream **sid** software repository, add the `sid-used sudo` command before your **apt** command:

Example: `sid-used sudo` **apt install package-name**

#### 3-16.3 Chromium browser interface display error

**Reason:**

Maybe U will see this issue on version 20200615 U3, Cuz we changed mesalib, should used another way to set Chromium.

**Solution:**

Run command:

```
sudo sed -i  \
's/"hardware_acceleration_mode":{"enabled":true},/"hardware_acceleration_mode":{"enabled":false},/' \
/home/pi/.config/chromium/Local\ State
```

Then re-open your Chromium browser.

#### 3-16.4 Bluetooth Audio connection lost

**Reason:**

Pi's Bluetooth has compatibility issues with certain hardware between alsa and pulseaudio.

**Solution:**

Disable Bluealsa Service, just use pulseaudio for bluetooth audio. Run the command below and reboot:

```
systemctl mask  bluealsa.service
```

**Note**： Here U must use **"mask"** for unactive bluealsa.service, mustn't use **"disable"** !!

### 3-17. Extra Application Instructions

#### 3-17.1 WPS Office Arm 64-bit Desktop Installation Note

Get the install package from download repo's "APP" folder, after extracting the installation package, go to the installation package directory.

Then connect to the public network and execute the following command as the root user:

```shell
sudo ./install.sh
```

The program will be installed.

**Note:** *Test only on the* **macOS Mojave theme custom desktop** *version!!* 

**For testing and learning use only!!!**

#### 3-17.2 How to install the QQ Official Desktop App (Linux Edition)

Make sure your system can connect to internet, then run the commands below as root user:

```
qq_pkg='linuxqq_2.0.0-b1-1024_arm64.deb' ; \
cd ~ ; \
wget https://raw.githubusercontent.com/openfans-community-offical/Debian-Pi-Aarch64/master/add-app/$qq_pkg ; \
apt install ./$qq_pkg -y ; \
rm -rf ./$qq_pkg
```

After this, the App will be finished the installation.

![linux_qq](./images/linux_qq.jpg)

----

## 4. Virtual Machine Instructions

Virtual machine resource packages are typically published as compression packages, and the following commands are performed to install the support for the unzip pack:

```
apt update ; apt install tar gzip zip unzip bzip2 xz-utils -y
```

### 4-1. Standard Virtual Machines PKG Instructions

Default user: root (remote permissions turned on), password: raspberry

After unzipping the virtual machine resource package, change location and into the virtual machine's resource package directory then unzip the virtual disk image:

```
xz -d -k disk.qcow2.xz
```

You will get a virtual disk image of **disk.qcow2**, and the system can be restored at any time with the commands above.

**Run the virtual machine:**

```
sudo ./vm-run

## This script command above will run the virtual machine in a background manner by default.
```

Run the virtual machine in the way the previous station:

Copy the file **vm_run** and name as **vm_run2** , open the file **vm_run2** and delete the following 2 lines:

```
... ## omitting content
nohup \
... ## omitting content
   &
... ## omitting content
```

Then, run **"sudo ./vm_run2"**.

**Remote login:**

Port 22 of the virtual machine has been mapped by default to the local port 2222, SSH access to the local machine's port 2222 directly.

Example of the command:

```
ssh -p 2222 root@local-ip-address
```
----
### 4-2 BT-Panel Virtual Machine PKG Instructions

In order to take care of new users and respond to the voices of the people, we finally “integrated” the Pagoda for you, using the virtual machine, 32-bit super clean custom ARMHF virtual system optimized for the pagoda, even for virtual machines, The speed is also greatly stronger than the official backplane system (who has used and who will understand :) --).

To run the benchmark:

![BT-Panel](./images/bt_mark.png)

By default, all software is installed. Version 5.9.X Relatively stable professional "learning version", you know, this is just only allowed to use for your testing!!

**Why BT-Panel?**

```
1. The use of beginners is convenient;
2. The voice of the masses is too high;
3. By the way...
```

**Why not integrate directly in the 64-bit OS?**

```
1. Not everyone needs a default integration, too bloated;

2. Pollute system;

3. BT-Panel is extremely poorly compatible with ARM64!

4. The BT-Panel is not just a simple installation. 
The software that needs to be used in the ARM system almost all needs to be recompiled. 
The compatibility is poor and it takes a long time. 
It can pretend that you doubt life and pretend that you wanna cry.

5. The problems of various strange pits encountered in our use;

6. It is not that the BT-Panel is not good overall. 
At least the compatibility on the ARM64 is a considerable problem. 
It feels like the official has not done the test. 
All the work just like do the testing for them by free.
```

**Instructions:**

As with the standard virtual machine, extract the compressed package, and then change location and into the virtual machine's directory to perform related operations.

**installation:**

```
sudo ./install
```

**Start BT-Panel Virtual Machine:**

```
./bt_run
```

**Close the BT-Panel Virtual Machine:**

To ensure the data synchronization security of the virtual machine, please follow the steps below:

```
Please ssh login to the virtual machine and execute the command "init 0" 
to shut down the virtual machine.

After shutting down, you need to execute the " ./bt_prog " command in the 
BT-Panel virtual machine directory 
to check if the virtual machine is closed.

If there is no output, it means the virtual machine has been shut down normally.

If the virtual machine cannot be shut down gracefully, 
execute the " ./bt_prog kill " command in the BT-Panel virtual machine directory.

Also remember to execute the " ./bt_prog " command again to check 
if the virtual machine is down.
```

**Automatic startup:**

```
## Enable boot auto start
./install int

## Cancel the boot automatically
./install uint
```

**Default parameter value:**

|Project|Content|
|---|---|
|Default Management Port|28888|
|Default Management Address|http://IP-Address-of-your-Raspberry-Pi:28888/|
|Default Web Management User and Password|openfans/openfans|
|BT-Panel Virtual Machine SSH Port|2222|
|BT-Panel virtual machine root default password|raspberry|

**How to use ssh to connect to BT-Panel virtual machine?**

```
Local connection: ssh -p 2222 root@localhost
External connection: ssh -p 2222 root@IP-address-of-your-Raspberry-Pi
```

**NOTE:**

```
Do not modify the default management port of the BT-Panel Panel unless you know how to modify the 
install the deployment script.

If you need to enable site support for custom ports, edit the ports file to add your custom port, 
but don't modify the other default ports in the ports file.
```

**To save and save everyone's time, all the functions of the BT-Panel are turned on by default.**

**For better performance, we strongly recommend turning off or removing features you don't need.**

----

### 4-3 How To Expand The Size Of A Virtual Machine Disk

First, make sure your virtual machine was shutdown or not running.

The virtual machine disk in this article uses **bt.qcow2.disk** as an example.

#### 4-3.1. Disk expansion

**View disk size**

Excuting an order:

```shell
qemu-img info bt.qcow2.disk
```

Get the following information:

```shell
Image: bt.qcow2.disk
File format: qcow2
Virtual size: 10G (10737418240 bytes) # Total disk size
Disk size: 6.4 # used capacity
Cluster_size: 65536
Format specific information:
    Compat: 1.1
    Lazy refcounts: false
    Refcount bits: 16
    Corrupt: false
```

**Disk expansion**

In this case, our goal is to add 10G capacity to the virtual machine disk.

Execute the following command:

```shell
qemu-img resize bt.qcow2.disk +10G
```

Then look at the disk size again

Excuting an order:

```shell
qemu-img info bt.qcow2.disk
```

The results are as follows:

```shell
Image: bt.qcow2.disk
File format: qcow2
Virtual size: 20G (21474836480 bytes) # Capacity increase is successful, the total size is 20G
Disk size: 6.4G
Cluster_size: 65536
Format specific information:
    Compat: 1.1
    Lazy refcounts: false
    Refcount bits: 16
    Corrupt: false
```

#### 4-3.2. Extended partition

**Expanding increased capacity to system partition**

First, start the virtual machine and login to the virtual machine.

```shell
ssh -p 2222 root@localhost
```

**View disk size**

Excuting an order:

```shell
fdisk -l /dev/sda
```

The results are as follows:

```shell
Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors # has been added to 20G
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcd0e4df1

Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 20969471 20967424 10G 83 Linux # Partition capacity has not been expanded
```

**View partition size**

Excuting an order:

```shell
df -hT
```

The results are as follows:

```shell
Filesystem Type Size Used Avail Use% Mounted on
Udev devtmpfs 496M 0 496M 0% /dev
Tmpfs tmpfs 103M 1.5M 101M 2% /run
/dev/sda1 btrfs 10G 4.7G 4.7G 50% / # Partition capacity has not been expanded
Tmpfs tmpfs 513M 4.0K 513M 1% /dev/shm
Tmpfs tmpfs 5.0M 0 5.0M 0% /run/lock
Tmpfs tmpfs 513M 0 513M 0% /sys/fs/cgroup
Tmpfs tmpfs 103M 0 103M 0% /run/user/0
```

**Installation** *parted* **Disk Management Tool**

```shell
apt update ; apt install parted -y
```

**Extended partition**

Enter the following command: **parted** and follow these steps:

```shell
parted
```

At this point, you can see the disk information as follows

```shell
GNU Parted 3.2
Using /dev/sda # This is the disk we need to operate
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print # Enter "print" to view the disk information of the current operation
Model: QEMU QEMU HARDDISK (scsi)
Disk /dev/sda: 21.5GB # Total size has been increased to 20G
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type File system Flags
 1 1049kB 10.7GB 10.7GB primary btrfs boot 
# Here "1" is the disk partition number, and the partition capacity has not changed yet.
```

Next enter the following command **resizepart** :

```shell
(parted) resizepart 
# Enter the command "resizepart" for partition expansion
Partition number? 1 
# Enter the partition number to be expanded. Since our disk here has only one partition, enter "1".
Warning: Partition /dev/sda1 is being used. Are you sure you want to continue?
Yes/No? yes # Confirm to continue, type "yes"
End? [10.7GB]? 100% 
# Enter "100%" to extend all available capacity to the partition specified in the previous step.
(parted) print 
# Enter "print" to view the disk information of the current operation
Model: QEMU QEMU HARDDISK (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number Start End Size Type File system Flags
 1 1049kB 21.5GB 21.5GB primary btrfs boot 
# You can see that the increased disk capacity has been expanded successfully.

(parted) quit # Enter "quit" to quit
Information: You may need to update /etc/fstab.
```

**Update Partition Table**

Execute the following command

```shell
partprobe /dev/sda
partprobe /dev/sda1
```

**Extended File System**

Our virtual machine here uses the *btrfs* file system. The related *btrfs* file system expansion operation is as follows:

Excuting an order

```shell
btrfs filesystem resize max /
```

Will get the following tips

```shell
resize '/' of 'max'
```

**Remount the partition**

This article extends the root partition **"/"**, so next we remount **"/"** root partition

Excuting an order:

```shell
mount -o remount,rw /
```

**Synchronous Data**

Excuting an order:

```shell
sync
```

**Validation results**

Check partition size

input the command

```shell
df -hT
```

The results are as follows:

```shell
Filesystem Type Size Used Avail Use% Mounted on
Udev devtmpfs 496M 0 496M 0% /dev
Tmpfs tmpfs 103M 1.5M 101M 2% /run
/dev/sda1 btrfs 20G 4.7G 15G 25% / # partition has been successfully expanded
Tmpfs tmpfs 513M 4.0K 513M 1% /dev/shm
Tmpfs tmpfs 5.0M 0 5.0M 0% /run/lock
Tmpfs tmpfs 513M 0 513M 0% /sys/fs/cgroup
Tmpfs tmpfs 103M 0 103M 0% /run/user/0
```

Restart the virtual machine, log in again, and execute the command **df -hT** to determine the result

----

## 5. Update And Upgrade

### 5-1 Upgrade System

For system updates, please use the tools or commands with the system, such as "apt update; apt upgrade"

**Due to Deepin compatibility issues, do not perform any system upgrades on Deepin Desktop!!**

### 5-2 Update Kernel And Firmware

Download the kernel and firmware update package, extract and go to the updated package directory, execute the following command:

```
cd ./upkg
sudo sh ./sys_upgrade
```

After the completion, restart it.

#### Note:

**Version 2.0 does not currently support upgrading from any other version and requires a new installation.**

### 5-3 Update Instructions

Click **[here](./update.md)** to see the update instructions.

### 5-4 Latest Current Version

Click **[here](./versions.md)** to view the latest current version information.

### 5-5 Rpi4 USB Boot Support (Upgrade eeprom FW)

Click **[here](./FW/)** to download file for eeprom FW upgrade, will be support Rpi4 usb boot.

After decompressing the files, please read the readme.txt file and follow the note steps to upgrade. (Note: You must upgrade the firmware on TF boot mode first)

----

## 6. Download Links

- MEGA : [Click to download](https://mega.nz/folder/coVQAaZR#ifOeikkhJpGYw8B7vvlDOg)

- Baidu network disk: [Click to download](https://pan.baidu.com/s/11Rt0cHnSPWyRAwhfCtTgJQ) *sharePassword:* **7nh7**

- OneDrive: [Click to download](https://1drv.ms/u/s!AtEthomfQXh8lWj8KVMcbJL0pgJL?e=tZHisM)

- Google Drive: [Click to download](https://drive.google.com/drive/folders/1MvMuzWYbjWSMZmY607qjukKiwSajOFZc?usp=sharing)

- HUAWEI OSS STORAGE: [View](https://pifan.cn.obs.cn-north-1.myhuaweicloud.com/)

 (Because of space constraints, **OneDrive** does not currently provide virtual machine image template to download)

----

## 7. Other Instructions

### 7-1 Donation

#### Thanks for your donation! We'll get the greatest power from your encourage!

You can choose to scan Alipay for direct sponsorship to support us, and we guarantee that all donations will be used for project development and equipment purchase.

![jz](./images/jz.png)

### 7-2 Contact Info.

Raspberry Pi Fan Base 64-bit OS special official community **QQ group:** *703626518(Full)* , **976102807(new)**

Raspberry Pi Fan Base official website: **[www.pifan.org](http://www.pifan.org)**

Technology support documents official website: **[blog.pifan.org](http://blog.pifan.org)**

Raspberry Pi Fan Base official forum: **[bbs.pifan.org](http://bbs.pifan.org)**

OPENFANS official website: **[www.openfans.org](http://www.openfans.org)**

### 7-3 Copyright

```
1. The all above system is built by the OPENFANS open source community and is exclusively 
distributed and provided technical support by the Raspberry Pi Fan base community;

2. Any words or image reprint must indicate the source of the system (software); 
you can make any modifications to the software or system, but you must keep the source and readme;

Strictly used for any commercial purpose, if you need to use it commercially, 
please contact and obtain permission from OPENFANS open source community and 
Raspberry Pi Fan base community;

3. The above system and the ownership of the software belong to the corresponding software 
author and the license agreement to comply with the relevant software package;

4. Failure to comply with the appeal rules, the OPENFANS open source community and the 
Raspberry Pi Fan base community have the right to pursue their respective responsibilities 
and order to stop all infringements;

5. OPENFANS open source community and Raspberry Pi Fan base community have the final 
interpretation of the above content.
```

## 8. Join US!

The Raspberry Pi Fan base community is recruiting **volunteers** to join the community now. The basic requirements are as follows:

- **Hardware development and design staff**

```
1. Recognize the Raspberry Pi Fan base community culture and have great enthusiasm 
for the Raspberry Pi;
2. Responsible and responsible for the task of completing community arrangements on 
time and in quality;
3. Have the design ability of 3D printing modeling or circuit DSP;
4. Have practical hardware design experience.
```

- **Software and system developer**

```
1. Recognize the Raspberry Pi Fan base community culture and have great enthusiasm 
for the Raspberry Pi;
2. Responsible and responsible for the task of completing community arrangements on 
time and in quality;
3. Familiar with system build compilation or software development;
4. We like the development language, including but not limited to: JAVA, Python, 
Go, NodeJS, C, C++ ...;
5. Require software compilation and Deb packaging;
6. Have practical development experience.
```

**Another way, organizations, institutions and business units are welcome to discuss cooperation!!!**

Please contact us with any intent: **[admin@openfans.org](mailto:admin@openfans.org)**

Please write down the details and intentions and at least leave your **mobile phone number**, thank you for your cooperation.

----

## 9. Thanks

OSCHINA : [Support fot git repo](https://gitee.com/)

Raspbian: Official system (automatic expansion script part reference)

UMRnInside :Project [UMRnInside/RPi-arm64](https://github.com/UMRnInside/RPi-arm64)(refer to the automatic expansion script section)

Andreiw: Project [andreiw/RaspberryPiPkg](https://github.com/andreiw/RaspberryPiPkg)(EFI firmware referenced in version 1.0)

Sakaki(1) : [link](https://www.raspberrypi.org/forums/viewtopic.php?f=56&t=244478) (kernel boot problem reference)

Sakaki(2) : A H264-V4L2-M2M hardware acceleration command line video player.

Margetts99 : [link](http://bbs.pifan.org/?thread-132.htm) (WPS integration recommendations and sharing issues report)

Windows Arm On Qemu: *see [link1](https://github.com/virtio-win/kvm-guest-drivers-windows/issues/177#issuecomment-468149012) & [link2](https://www.raspberrypi.org/forums/viewtopic.php?f=56&t=248345&sid=d4dd0681937f13e9c0cb4f04e5b54979)*

**And all other friends who have privately sponsored and helped us!**

----

Once again despise the attack and slander called the "Dog Egg Brother" !


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)