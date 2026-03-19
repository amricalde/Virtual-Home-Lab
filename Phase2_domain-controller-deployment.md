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

  After that installing, you are prompted to promote the server as a domain controller
  ![notif-dc](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p2s6.jpg?raw=true)

<!--
**Prerequisites Check; troubleshooting "The TCP/IP networkig protocol must be properly configured..."**
Unfortunately after trying to promote it to DC, I ran into an error

**Re-attempting to promote the server**
after troubleshooting, i tried again and it was successful (show screenshot of login screen amr/administrator)
-->

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
