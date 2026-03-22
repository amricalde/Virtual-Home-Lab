<!--
Things I did as of 03/21/26:
- download Windows 11 client         -> should add that on Phase 1?
- created new vm for client, chose windows 11 pro
- created new psw policy
- created ashley.admin
- added it as member of domain admins
- logged on ashley.admin , disabled local administrator
- joined client to domain > need more explanation, settings > fajief > add to domain
  - pinged server from client to see if they were communnicating
  - errors: it was not the right config. dns was wrong, ip of client was wrong, host-only for NAT on client VM
- now that client is in the domain, i can sign as any user on the domain (can be ashley or KRISTI BOMBACLOT)
- ashleymadison@AMR.local    UselessUser123#@!
- moved Windowslicent to yyz computers
- did some cleaning up/re-organize in aduc
- gpudate /force; update the policies from its group policy management
 
  - screenshots:
  -   ip address of client and server
  -   members of domain admins
  -   pswd policy settings
  -   pwsd policy on client - shows what policy is implemented on that computer
 
- next task:
  - add wifi to workstation
  - documentation; separate phase 4 and 5 cus its all meshed here.
-->
