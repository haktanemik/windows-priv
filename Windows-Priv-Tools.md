# Windows Privilege Escalation Tools

## winPEAS
```
winpeas.exe
```

## Windows Exploit Suggester
```
./windows-exploit-suggester.py --update
./windows-exploit-suggester.py --database <db-file.xlsx> --systeminfo <system-info-file>
```
## Sherlock
```
powershell.exe -exec bypass -Command "& {Import-Module .\Sherlock.ps1; Find-AllVulns}"
```

## JAWS
```
powershell.exe -ExecutionPolicy Bypass -File .\jaws-enum.ps1 -OutputFilename <output-file>
```

## PowerSploit - PowerUp
```
powershell.exe -exec bypass -Command "& {Import-Module .\PowerUp.ps1; Invoke-AllChecks}"                                                                   ```
```

## Metasploit
```
post/multi/recon/local_exploit_suggester
post/windows/gather/enum_patches
```
### See also
* [winPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/winPEAS)
* [Windows Exploit Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)
* [Sherlock](https://github.com/rasta-mouse/Sherlock)
* [JAWS](https://github.com/411Hall/JAWS)
* [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)
