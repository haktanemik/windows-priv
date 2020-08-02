## Enumeration
Sytem Informations (OS Version, architecture, Hotfixs, domain etc)
```
systeminfo
```

Hostname
```
hostname
```

Installed Patches on system
```
wmic qfe
```

Process & Services Enumeration
```
tasklist /SVC # list running process
sc query # list services
schtasks /query /fo LIST /v # list scheduled tasks
sc query <service name> # Service information
sc config <service name> binpath= "HERE" # change binpath of service
sc stop <service name> & sc start <service name> # service restart
```

List softwares
```
dir /a "C:\Program Files"
dir /a "C:\Program Files (x86)"
```


Unquoted Service Paths
```
wmic service get name,displayname,pathname,startmode |findstr /i "Auto" | findstr /i /v "C:\Windows\\" |findstr /i /v """
```

Display Shared Resources
```
net share # on the local computer
net view \\<host> # specified computer
```

Port & Connection State
```
netstat -anto
```
Users & Groups Enumeration
```
echo %username% # connected User
echo %userdomain% # domain name
echo %logonserver% # domain controller
net users # list local users
net users <username> # specific user's information
net users /domain # list users in domain
net localgroup administrators # list users members in administrators group
net groups /domain # list groups in domain
net group “Domain Admins” /domain # list users members in Domain Admins group 
net group “Domain Computers” /domain # list computers in domain
net group “Domain Controllers” /domain # list Domain Controllers
net accounts # account policies and password policies.
nltest /domain_trusts # list of trusted domains
whoami /priv # account's Privileges
```

Network Information
```
ipconfig /all # list all network interfaces
route print # list routing table
arp -a # list ARP table
netsh wlan show profile # list SSID
netsh wlan show profiles name=<SSID name> key=clear # show SSID's password
```

Firewall Information
```
netsh firewall show state
netsh firewall show config
```

Show all drivers
```
driverquery
```
