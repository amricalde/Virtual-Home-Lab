<!-- 

Phase 5 - Group Policy configuration and implementation
- created new psw policy (pswd length 12, expiry 90 days)
  -  pswd policy > enforced
  - gpudate /force; update the policies from its group policy management >> checked on clients side
  - since the password was reset by user on first logon on the client machine, we need to set "User must change password on next logon" to apply the updated password policy. now that its set, the user will be prompted to change the password based on the standards of the policies implemented.
- created wallpaper policy

  - screenshots:
  -   pswd policy settings
  -   pwsd policy on client - shows what policy is implemented on that computer

- next task:
  - add wallpaper gpo
  - add wifi to workstation

-->
