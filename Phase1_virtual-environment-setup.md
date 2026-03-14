Phase 1 Virtual Environment Setup
-
The first phase focuses on preparing the virtual environment used throughout the entire lab. Since the objective of this project is to simulate a small Active Directory environment, VMWare Workstation Pro 17 was used to host these virtual machines.

Four main points for this section:
- Download VMware application ✅
- Download Windows Server ISO ✅
- Create a new VM
- Installing Windows Server on VM

**Downloading VMWAre Workstation Pro 17**
- Ensure virtualization is enabled on your PC by checking task manager.
![alt text](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s1.jpg?raw=true)
  _note: to enable virtualization on your PC, go to BIOS > search "SVM mode" and enable it from there._
- Download the latest version, I used [broadcom.com](https://support.broadcom.com/web/ecx/home#.) to install it for free. More steps could be found [here](https://osintteam.blog/my-virtual-homelab-introduction-caa2f34c73c3) if needed
<br>

**Downloading Windows Server 2022 ISO**
- Windows installation link : [https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
- I chose the ISO downloads 64-bit edition

Once the download is done, I created a new VM to startup the process.

**Creating a new virtual machine**
- Open application currently installed
- Create a new virtual machine > typical > I will install the os later > Microsoft Windows, Windows Server 2022 > deafult >
  Max disk size: 20GB, Split virtual disk into multiple files > finish <br>
  
After clicking finish, VMWAre loads the new machine with the specifications applied and it looked like this.
![VMWare-screen](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p1s7.jpg?raw=true)

