Phase 5 - Group Policy configuration and implementation
-
Phase 5 involves creating and implementing two different type of Group Policies using Group Policy Management. These policies are applied to appropriate objects(users, computers, or groups) depending on their level within the domain. This segment demonstrates how centralized management allows administrators to efficiently control and enforce configurations in one place.

The two GPOs that are created:
- Password Policy ✅
- Wallpaper Policy ✅

Bonus Point:
- Connecting to the internet ✅

<br>

**Creating and implementing Password Policy**
- Creating the password policy was straightforward, I just had to make sure you found the right location to configure the policy itself.
- Head to GPM, right click on AMR.local domain, create policy
- Once it is added, right click to edit.
- Computer configuration > windows settings > account policies
- Set minimum password length: 12, maximum password age 90 days.
  ![GPM-psw-config](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s07.jpg?raw=true)
- Since the password was already set by user on first logon using the client machine, I set it to "User must change password on next logon" in the user's settings in Active Directory to apply the updated password policy. After that's set, the user was prompted to change the password based on the standards of the policies implemented. Otherwise, the policy would have been implemented after the password has expired.

<br>

**Creating and implementing Wallpaper Policy**
- To start, I downloaded a background image first. This was done through downloading an image through the internet (_more guide on connecting to the internet is provided below_).
- Created a shared folder called "Common Share Files" under C: path in the server
- right click folder > Properties > Sharing > Advanced Sharing > check Share this folder > Share name: Common_Share_Files$ > Apply
- It then generates a network path and looks like this: <br>
  ![shared-folder-config](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p5s03.jpg?raw=true)
- Also ensure that the folder has Read permissions checked so the photo is accessible for all computers
  ![read-permi](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p5s04.jpg?raw=true)
- The reason why a network path is preffered over local path is to keep it consistent throughout all computers. For centralized management, network sharing allows the wallpaper to be updated for the entire organization that is kept in one location. Having a shared folder also ensures that the wallpaper is accessible to all computers rather than locally where you have to manually set every computer in the domain.
- Made Wallpaper Policy in the AMR.local domain
- User Config > Policies > Desktop > Desktop > Desktop Wallpaper > Enabled > Wallpaper Name: path_of_your_photo\wallpaper.jpg > Wallpaper style: Fill
- After creating, head to client to see changes.. restart machine or gpupdate /force if needed.
  ![wallpaper-policy-success](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p5s05.jpg?raw=true)

<br>

**Bonus point: Connecting the server to the internet**
- Add another network adapter on the designated VM, in this case our server VM; NAT2.
- So now we have <br>
      _ethernet0_  - host-only to communicate with other computers here. (static IP, DNS: Server's IP) <br>
      _ethernet1_  - NAT to connect to internet. (DHCP automatic, DNS: still Server's IP addr)
- To test: ping google.ca was successful, ipconfig (to check both network adapters are present), could also check configurations on network connections


<!-- 

Phase 5 - Group Policy configuration and implementation
- created new psw policy (pswd length 12, expiry 90 days)
  -  pswd policy > enforced
  - gpudate /force; update the policies from its group policy management >> checked on clients side
  - since the password was reset by user on first logon on the client machine, we need to set "User must change password on next logon" to apply the updated password policy. now that its set, the user will be prompted to change the password based on the standards of the policies implemented.

- connected to internet first
  - created another network adapter; nat2  ( right click on server VM > settings > add network adapter)
      so basically rn:
      ethernet0  - host-only to communicate with other computers here. (static IP, DNS: Server's IP) 
      ethernet1  - NAT to connect to internet. (DHCP automatic, DNS: still Server's IP addr)
  - to test: ping successful, ipconfig (to check there's one)

- created wallpaper policy
  - downloaded background image
  - created file as shared folder, and appropriate permissions
  -created wallpaper policy 
    - User Config > Policies > Desktop > Desktop > Desktop Wallpaper > Enabled > Wallpaper Name: path_of_your_photo\wallpaper.jpg > Wallpaper style: Fill
    - for the wallpaper name, use network path rather than local to keep it consistent throughout all computers. For centralized management, network sharing allows the wallpaper to be updated for the entire organization that is kept in one location. Having a shared folder also ensures that the wallpaper is accessible to all computers rather than locally where you have to manually set every computer in the domain.
    - after creating, head to client to see changes.. restart machine if needed.


rsop?

  - screenshots:
  -   pswd policy settings
  -   pwsd policy on client - shows what policy is implemented on that computer

- next task:
  - add wallpaper gpo
  - add wifi to workstation

-->
