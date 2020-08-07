# Windows Kernel Vulnerabilities

### List all installed patches
```
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

### Search for a specific update package 
```
wmic qfe get Caption,Description,HotFixID,InstalledOn | findstr /C:"<HotFixID>" /C:"<HotFixID>"
```
### Windows Exploits Repo
```
https://github.com/SecWiki/windows-kernel-exploits
```

### Automated Tools

* Windows Exploit Suggester
* Sherlock
* PowerSploit - PowerUp

*For usage information:*
```
https://github.com/haktanemik/windows-priv/blob/master/Windows-Priv-Tools.md
```
### Metasploit
```
post/windows/gather/enum_patches # Determine missing hotfix
post/multi/recon/local_exploit_suggester # Suggester
```
