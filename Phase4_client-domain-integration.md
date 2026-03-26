Phase 4 - Client domain integration
-
In Phase 4, the Windows Client was integrated into the Active Directory AMR.local domain. This enables domain authentication and allows the system to be managed centrally through the Domain Controller.

Three main points for this section:
- Create admin account ✅
- Join client to domain; troubleshooting "An Active Directory Domain Controller... AMR.local cannot be contacted" ✅
- Re-organize Active Directory objects ✅

**Creating admin account** <br>
Before jumping in to join the client to the domain, a domain admin account is created to manage and configure domain-joined systems. This will be helpful in the next main point(s) of this phase and it is for best practice.
- on the server, I created an account "ashley.admin" under YYZ > Users
- under Domain Admins group members, I added ashley.admin
  ![Domain-admins-a.admin-added](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s08.jpg?raw=true)
- administrator account is then disabled to apply principle of least privilege, which you can also see in the screenshot above (arrow down symbol beside User character).
  -  AMR.local > Users > right click Administrator > disable

<br>

**Joining Windows Client to domain; troubleshooting**
- in the client machine, I logged in as a localadmin
- under Settings > System > About > Domain or workgroup > sign in using ashey.admin credentials > Computer name > Change domain > Member of: AMR.local
- at first attempt, got an error <mark>"An Active Directory Domain Controller dor the domain "AMR.local" cannot be contacted"</mark>
  - to check if client and server were communicating, I **pinged the server** from the client machine; they were not communicating
  - used **ipconfig** to check that the client address was configured properly
  - realized errors: not the right configurations.
     - DNS was wrong, it must point to the server IP address
     - IP was not in the same subnet as the server
     - the client VM network adapter was not set to Host-only, the devices were not on the same network.
    <!-- related to next phase: disabled second network adapter nat... needed it to download wallpaper, having nAT really confused the client computer to join domain or properly communicate to it.-->
- after successful troubleshooting, the client machine is now in the domain and can sign as a user on the domain.
  ![domain-join-successful](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s01.jpg?raw=true)

<br>

**Re-organizing Active Directory**
- to ensure efficient control, and security, I did some re-organizing in the Active Directory.
- now that there is a new computer on the domain, I moved Windows 11 Client from AMR.local > Computers to YYZ > Computers OU
- created separate OUs for Security Groups and DL Groups, having the appropriate groups in the right OUs
- deleted Servers OU for now since I do not have any yet. Ran into this error <mark>"You do not have sufficient priviledges to delete Servers, or this object is protected from accidental deletion."</mark>
  ![insufficient-privileges](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s04.jpg?raw=true)
  - went back to original administrator account and added ashley.admin as a member of the same groups. 
    ![admin-groups](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s05.jpg?raw=true)
  - the step above still didn't work, so I went to View > Advanced Features > Servers OU > Properties > Objects > uncheck "Protect object from accidental deletion" and it worked!
    ![accidental-deletion](https://github.com/amricalde/Virtual-Home-Lab/blob/main/screenshots/p4s09.jpg?raw=true)



<!--

- joined client to domain, settings > system > about domain or workgroup > add to domain > sign in to admin
  - at first, it gave the error "an active directory controller cannot be contacted" so i
  - pinged server from client to see if they were communnicating; they were not
  - did ipconfig to check that the adress of the client was configured properly
  - realized errors: it was not the right config. dns was wrong, ip of client was wrong, and forgot to do host-only for NAT on client VM
- now that client is in the domain, i can sign as any user on the domain (can be ashley or KRISTI BOMBACLOT)
- ashleymadison@AMR.local    UselessUser123#@!

- moved Windowslicent from domain computers to yyz computers OU      

cleaning up/ reorganizing
- did some cleaning up/re-organize in aduc        > got error i dont have privileges to do this blablabla


  - screenshots:
  -   ip address of client and server
  -   members of domain admins

-->
