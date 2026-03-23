Phase 4 - Client domain integration
-
In Phase 4, the Windows Client was integrated into the Active Directory AMR.local domain. This step enables domain authentication and allows the system to be managed centrally through the Domain Controller.

Three main points for this section:
- Create admin account
- Join client to domain; troubleshooting "An Active Directory Domain Controller... AMR.local cannot be contacted"
- Re-organize Active Directory objects


<!--
Things I did as of 03/21/26:

Phase 4 - Client setup

So i could sign in for client to setup domain
- created ashley.admin
- added it as member of domain admins
- logged on ashley.admin , disabled local administrator

- joined client to domain > need more explanation, settings > system > about domain or workgroup > add to domain > sign in to admin
  - pinged server from client to see if they were communnicating
  - errors: it was not the right config. dns was wrong, ip of client was wrong, host-only for NAT on client VM
- now that client is in the domain, i can sign as any user on the domain (can be ashley or KRISTI BOMBACLOT)
- ashleymadison@AMR.local    UselessUser123#@!
- moved Windowslicent from domain computers to yyz computers OU

sidenote for phase 4
- did some cleaning up/re-organize in aduc


  - screenshots:
  -   ip address of client and server
  -   members of domain admins

-->
