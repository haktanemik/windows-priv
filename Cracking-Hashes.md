# Cracking Hashes

## LM
John
```
john --format=lm <hash file>
```
Hashcat
```
hashcat -m 3000 -a 3 <hash file>
```
## NTLM
John
```
john --format=nt <hash file>
```
Hashcat
```
hashcat -m 1000 -a 3 <hash file>
```

## NetNTLMv1
John
```
john --format=netntlm <hash file>
```
Hashcat
```
hashcat -m 5500 -a 3 <hash file>
```
## NetNTLMv2
John
```
john --format=netntlmv2 <hash file>
```
Hashcat
```
hashcat -m 5600 -a 3 <hash file>
```
