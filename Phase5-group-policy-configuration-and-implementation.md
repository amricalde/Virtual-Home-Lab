Phase 5 - Group Policy configuration and implementation
-


<!-- 

Phase 5 - Group Policy configuration and implementation
- created new psw policy (pswd length 12, expiry 90 days)
  -  pswd policy > enforced
  - gpudate /force; update the policies from its group policy management >> checked on clients side
  - since the password was reset by user on first logon on the client machine, we need to set "User must change password on next logon" to apply the updated password policy. now that its set, the user will be prompted to change the password based on the standards of the policies implemented.

- connected to internet first
  - created another network adapter; nat2
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
