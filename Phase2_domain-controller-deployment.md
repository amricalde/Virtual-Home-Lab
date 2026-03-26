Phase 2 Domain Controller deployment
-
In Phase 2, Windows Server was configured as a Domain Controller by installing Active Directory Domain Services and promoting the server to host a new domain. This establishes the core environment for centralized authentication and management.

Three main points for this section:
- Install Active Directory Domain Services and DNS Server ✅
- Prerequisites Check; troubleshooting "The TCP/IP networkig protocol must be properly configured..." ✅
- Promote the server to a Domain Controller ✅


**Installing AD DS and DNS Server**
- Under Server Manager > Manage > Add Roles and Features > Select server roles: Active Directory Domain Services and DNS Server.
- When adding AD DS, additional roles and management tools are automatically included to support its functionality.
- In the end, it looked something like this:
  ![tools-confirmation](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s5.jpg?raw=true)

- When installation is complete, you are prompted to promote the server as a domain controller
  ![notif-dc](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s6.jpg?raw=true)

<br>

**Prerequisites Check; troubleshooting**
- Unfortunately after trying to promote it to DC, I ran into an error and failed the prerequisites check.
  ![troubleshooting-TCP/IP](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s7.jpg?raw=true)
- <mark> "The TCP/IP networking protocol must be properly configured..."</mark> indicates that the server's network needs to be reconfigured to     meet the requirements for DC promotion. To properly promote a server into a DC, it must have a static IP and a DNS that points to itself or to   another DC.
- What I did:
  - checked network connection; there was a red icon and said "Network cable unplugged".
  - changed the IPv4 configuration to static and filled in the appropriate IP address and DNS and it still gave me the same output (red icon, network cable unplugged).
  - I later realized that I did not properly configure my VM and forgot to add a network interface.
  - changed NAT to host only to create private network between host computer and VM (this "plugs in" network cable virtually).
  - added a network; host only needs a virtual network to exist and make the network adapter valid.
    ![adding-VMnet1](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s9.jpg?raw=true)
  - After that, I re-configured the static IP and DNS again and it worked.
    ![IPv4-config](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s10.jpg?raw=true)

<br>

**Re-attempting to promote the server**
- After troubleshooting, I tried to promote the domain controller again and succesfully created an AD domain.
  ![domain-successful](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s13.jpg?raw=true)

<!-- 
What i did today(3/15/26):
- added AD DS, DNS, promoted to DC but ran into error below
- troubleshoot TCP/IP networking protocol; probably cus it was on DHCP, it needed static ip (ask why?)
  - added static ipv4 (-still red first time)
  - checked network connection; it was red, "Network cable unplugged"
  - changed NAT to host only
  - added network
  -(then added static ip) - red gone!
- went back Server Manager > AD DS > Under Servers, it would show a yellow warning sign, indicating to promote DC
- promoted to DC
  - followed steps, created AD domain: AMR.local
-->
