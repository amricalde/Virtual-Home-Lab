Phase 1 Virtual Environment Setup
-
The first phase focuses on preparing the virtual environment used throughout the entire lab. Since the objective of this project is to simulate a small Active Directory environment, VMWare Workstation Pro 17 was used to host these virtual machines.

Five main points for this section:
- Download VMware application ✅
- Download Windows Server ISO ✅
- Create a new VM ✅
- Install Windows Server on VM ✅
- Set up Windows Server ✅
- Set up Windows 11 Client ✅

**Downloading VMwAre Workstation Pro 17**
- Ensure virtualization is enabled on your PC by checking task manager.
![task-manager-screen](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s1.jpg?raw=true)
  _note: to enable virtualization on your PC, go to BIOS > search "SVM mode" and enable it from there._
- Download the latest version, I used [broadcom.com](https://support.broadcom.com/web/ecx/home#.) to install it for free. More steps could be found [here](https://osintteam.blog/my-virtual-homelab-introduction-caa2f34c73c3) if needed
<br>

**Downloading Windows Server 2022 ISO**
- Windows Server installation link : [https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
- I chose the ISO downloads 64-bit edition

Once the download is done, I created a new VM to startup the process.
<br>

**Creating a new virtual machine**
- Open application currently installed
- Create a new virtual machine > typical > I will install the os later > Microsoft Windows, Windows Server 2022 > deafult >
  Max disk size: 20GB, Split virtual disk into multiple files > finish <br>
  
After clicking finish, VMwAre loads the new machine with the specifications applied and it looked like this.
![VMWare-screen](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s7.jpg?raw=true)

<br>

**Installing Windows Server on VM**
- Head to the virtual machine settings by right clicking on the VM name.
- Settings > Hardware > CD/DVD (SATA) > Use ISO image file > browse > downloads > SERVER_EVAL_x64FRE_en-us.iso > open > OK
  ![VM-iso-download](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s9.jpg?raw=true)
<br>

Et voila! It's now ready. Power on the virtual machine. While it is loading, constantly press any key to load the ISO. If it was missed and ISO was not loaded, simply restart and try again.

**Setting up Windows Server**
- Once the ISO is loaded, it will take you to the OS setup, click Next.
- Select the Windows Server 2022 Standard Evaluation (Desktop Experience). The first option only has the command line interface and the second one that is selected, provides the graphical user interface. <br>
  ![OS-setup-gui](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s11.jpg?raw=true) <br>
- Accept the terms > Next > Custom: Install Microsoft Server Operating System only (advanced) > Next
- After loading, it will prompt to Customize settings, creating username and password. <br>
  Username: Administrator <br>
  Password: ******* <!-- Admin43*@ <br> -->
- Once the steps above are complete, AD tools are ready to be downloaded.

**Setting up Windows 11 Client**
- The process is similar to the ones above.
- Windows 11 installation link: [https://www.microsoft.com/en-ca/software-download/windows11](https://www.microsoft.com/en-ca/software-download/windows11)
- Went to "Download Windows 11 Disk Image (ISO) for x64 devices" and followed from there.
- After downloading the ISO, create a new VM
    - Typical > Installer disk image file: (find the w11 iso) > deafault > default > finish
- Notes:
    - when it goes to the windows set up, select product key > Windows 11 Pro > custom
    - choose "Set up device for work or school"
    - for signing in go to sign in options > domain join instead > name: localadmin > security questions > turn off all privacy settings for device
- Once your client machine is all set up, it will be ready to use for Phase 4 and 5.

<!--
Helpful commands
-
winver     checks the windows version
-->
