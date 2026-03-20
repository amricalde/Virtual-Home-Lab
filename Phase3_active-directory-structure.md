<!-- 
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
    Services (nested OU)
  |
  LGA (OU)
    |
    Users (nested OU)
      |
      Kristi Rodos (user)
      IT; IT_LGA (group)
      DL-ITadmins; DL-ITadmins_LGA (group)
    Computers (nested OU)
    Services (nested OU)

"issues" encountered:
- screenshot 10; cannot create object IT because name is already in use. Basically you cannot have the same group name under one domain.
  solution: same group name (aka CN, common name, display name) which is fine, as long as group name (pre-Windows 2000) is unique. In our case,
  YYZ > Users > IT (pre-W: IT_YYZ)
  LGA > Users > IT (pre-W: IT_LGA)


-->
