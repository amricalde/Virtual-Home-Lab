Phase 3 - Active Directory structure
-
Phase 3 focuses on designing and implementing the Active Directory structure for the enterprise environment. The structure consists of 2 main Organizational Units, YYZ and LGA, each representing separate locations. Within each of these are three nested OUs: Users, Computers, and Servers. These OUs are used to manage and organize objects such as user accounts, security groups, and distribution groups.

<!--
Here is a sketch of how the Active Directory looks like:
(diagram) -->

Four main points for this section:
- Access Active Directory Users and Computers; troubleshooting "Naming information cannot be located..." ✅
- Build Active Directory structure ✅
- Add objects (users and groups) within the OUs ✅

<br>

**Accessing Active Directory Users and Computers; troubleshooting**
- When attempting to launch Active Directory Users and Computers, an error occured.<br>
  ![Error-ADUC-failed-to-start](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s01.jpg?raw=true)
- <mark>"Naming information cannot be located for the following reason: The server is not operational."</mark> suggests that the server is not functioning properly and cannot be used to acccess this tool.
- This is what I tried to resolve the issue:
    - checked network settings; network cable was unplugged once again.
    - made sure the right configurations were set. Looked for any errors in IPv4 addressing and DNS, network adapter, and virtual network. editor, everything were set as they should be.
    - tried to manually connect Ethernet 0 to VMnet1 as the VM was running, but was unsuccessful. I got this error instead. <br>
      ![Ethernet0-VMnet1-connection-failed](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s05.jpg?raw=true)<br>
    - <mark>"Could not connect to Ethernet0 to virtual network VMnet1"</mark> tells us that the server VM cannot connect to network adapter VMnet1 because something that is required to use it may be broken. Therefore, the issue lies on the VMware network on the host machine.
    - ran a few commands on host machine:   
      **_ipconfig_**: resulted in <mark>"Ethernet 0... Media disconnected"</mark>, confirms that VMware has no link to Ethernet 0. <br>
      _Win + R > **ncpa.cpl**_: looked for VMware Network Adapter VMnet1. It was not there, VMware network is broken.<br>
      _Win + R > **services.msc**_: opened serivces to if VMware DHCP Service and VMware NAT Service were running, as well as to restart.
      ![vmware-nat-service](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s06.jpg?raw=true)
    - ran into another error trying to reset the services. <mark>"Error 1068: The dependency service or group failed to start."</mark>
    - this meant that I could not change anything, so I reset the Windows network stack to fix error 1068 using the following commands: <br>
      **netsh winsock reset<br>
      netsh int ip reset**
    - restarted my computer, successfully reset both services.
    - VMware DHCP/NAT service > properties > general > startup type: Automatic
    - restored defaults on virtual network editor. <br>
      ![virtual-network-editor-restore](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s07.jpg?raw=true)
    - powered on VM and checked network connections, Ethernet0 is successfully connected again.
    - Active Directory Users and Computers is now accesible. 

<br>

**Building the Active Directory structure**
- Created 2 top-level OUs to represent the different locations. One for YYZ and the other for LGA.
- Added nested OUs within each location (Users, Computers, Servers)<br>
  ![OUs-top-nested](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s09(1).png?raw=true)

<br>

**Adding objects (users and groups) within the OUs**
- Within YYZ > Users, I created:
    - **Accounting** (Security Group - Global)
    - **Ashley Madison** (User)
    - **IT**; IT_YYZ (Security Group - Global)
    - **DL-ITadmins**; DL-ITadmins_YYZ (Distribution Group - Global)
- Within LGA > Users, I created:
    - **Accounting** (Security Group - Global)
    - **Kristi Rodos** (User)
    - **IT**; IT_LGA (Security Group - Global)
    - **DL-ITadmins**; DL-ITadmins_LGA (Distribution Group - Global)
- Notes on Groups
    - security group is used to assign permission(s) to shared resources.
    - distribution group is a distributed list that is used for sending email to a collection of users by using an app like Exchange.
    - global group scope indicates that the group is accessed within the domain.
    - domain global group scope can be accessed through different domains.
- Notes on SAM Account Names
    - when creating group names, it can have the same common name(CN) but the pre-Windows 2000 group name, also known as SAM (Security Account Management) Account Name has to be unique.
    - otherwise, it will show you this error. You cannot have the same SAM Account Name under the same domain.
      ![SAMaccountname-error](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s10.jpg?raw=true) <br>
    - in this scenario for example: <br>
      YYZ > Users > IT (pre-W: IT_YYZ)<br>
      LGA > Users > IT (pre-W: IT_LGA)<br>
      You can see that the IT group under YYZ Users, has a SAM Account Name of IT_YYZ and LGA Users has IT_LGA. The same goes for the DL-ITadmins and other groups that may be added.
      ![SAMaccountname-example](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s11.jpg?raw=true)
- When everything is configured, the Active Directory structure currently appears as follows:
  ![completeP3](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p3s09.jpg?raw=true)



<!-- ---------------------------------------------------------------------------------------------------------------------------------------
Notes as of 03/19/26:
- tried to run aduc but gave me that error (screenshot1)
- Win + R > ncpa.cpl > look for VMware Network Adapter VMnet1 ;;was not there, VMware network broken
- Win + R > services.msc > restart VMware DHCP Service and VMware NAT Service; did  not work either, error 5?
- checked network settings.. and ethernet0 was in fact unplugged. 
- tried excuting these commands 
    netsh winsock reset
    netsh int ip reset
  then restart
- trying to restore defaults now on virtual network editor,wtf gave me vmnet 8 , nat, nat, dhcp enabled, 192.168.17.0 ???????
- turned on vm anyways.. what the frick it worked??? LOL wthhh -- need to find out what happened, and what those commands mean

notes:
- error 1068
-"could not connect ethernet 0"
- media disconnected
basically main issue was on host not being able to run vmware services because of host networking issue/it stopped working - which essentially broke the vmnet adapters, so vm had no connection, no IP
okay,,,, moving on,,,,

- now in aduc, up and running
AMR.local
  |
  YYZ (OU)
    |
    Users (nested OU)
      |
      Ashley Madison (user)                       -> pswd: P@ssw0rd
      DL-ITadmins; DL-ITadmins_YYZ (group)        -> distributed list; used for sending email to a collection of users by using an app like Exchange.
      IT; IT_YYZ (group)
    Computers (nested OU)
      |
      Computer01                                  -> not sure if i should keep for now
    Servers (nested OU)
  |
  LGA (OU)
    |
    Users (nested OU)
      |
      Kristi Rodos (user)
      IT; IT_LGA (group)
      DL-ITadmins; DL-ITadmins_LGA (group)
    Computers (nested OU)
    Servers (nested OU)

"issues" encountered:
- screenshot 10; cannot create object IT because name is already in use. Basically you cannot have the same group name under one domain.
  solution: same group name (aka CN, common name, display name) which is fine, as long as group name (pre-Windows 2000) is unique. In our case,
  YYZ > Users > IT (pre-W: IT_YYZ)
  LGA > Users > IT (pre-W: IT_LGA)


-->
