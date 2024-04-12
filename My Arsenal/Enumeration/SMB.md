<h1>$${\color{blue}SMB}$$</h1>


```
nmap -p445 — script smb-protocols <target ip>
```

```
nmap -p139 — script smb-protocols <target ip>
```

```
nmap --script smb-enum-shares -p 139,445 <Target IP>
```

```
nmap -p 139,445 -vv -Pn --script=smb-vuln-cve2009-3103.nse,smb-vuln-ms06-025.nse,smb-vuln-ms07-029.nse,smb-vuln-ms08-067.nse,smb-vuln-ms10-054.nse,smb-vuln-ms10-061.nse,smb-vuln-ms17-010.nse {IP}
```

```
sudo nmap --script smb-vuln* -p 139,445 <Target IP>
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/f473b157-937b-46a4-bbbd-f6245cd645cd" >
</p> 

Or

```
nmap -sC -p 139,445 -sV 10.0.2.30
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/39868d95-e508-42f3-bcb4-eed45181a186" width=750 >
</p> 

Nice ! we found out the version of Samba running in the server. Now just go to google and search whether the given version is vulnerable or not.

That’s great , but what if the samba server was patched, or didn’t have a samba server to begin with?

There are many ways to enumerate the service itself. The quickest way is to use a tool called ```enum4linux```. However I have noticed that sometimes the output is not very pleasing. Other tools which I feel better are ```smbclient``` and ```smbmap```. I will also show how to manually access smb folder , but sometimes that fails. So primarily , you should be well versed with smbclient and smbmap , they are much more reliable.

As promised , let us first access it manually. To manually access the smb shares, go to folders and type this:

## 1.enum4linux usage:

```
enum4linux -a -U 10.10.10.10              for enum SMB username;
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/456ca70b-6061-4d99-b0be-4bf8b00cfd32"  >
</p> 

## 2.smbmap

```
smbmap -H 10.10.10.10 -R              -H hostname , -R recursive switch.
```

```
smbmap -H <target IP> -u username -p password
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/cceabd1a-991d-497f-b83c-33e22a7cd758" width=700 height=500 >
</p> 

## 3.smbclient usage:

```
smbclient -N -L \\\\10.10.10.10 
```

```
smbclient --no-pass -L //<IP> # Null user
```

```
smbclient -U '%' -N \\\\<IP>\\<SHARE> # null session to connect to a windows share
```

```
smbclient -L <target IP>
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/53ecaeb2-ba7e-4099-834f-83d7cc25d33f" >
</p> 

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/1cbc2c3e-fbc7-4d1c-bd45-37132fb091ad" >
</p> 

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/1798d351-1c30-43af-94fb-0aea257b035c" >
</p> 

## 4.crackmapexec usage:

```
crackmapexec smb <IP> -u '' -p '' --shares #Null user
```

installing: ```apt-get install crackmapexec```


************

# Brute forcing:
Name: Hydra Brute Force
Description: Need User
Command: 
```
hydra -t 1 -V -f -l {Username} -P {Big_Passwordlist} {IP} smb
```

```
nmap --script smb-brute -p 445 <IP>
```

```
legba smb --target share.company.com --username admin --password data/passwords.txt [--smb-workgroup <SMB_WORKGROUP>] [--smb-share <SMB_SHARE>]
```

***************
# Enumeration by metasploit
  Name: SMB/SMB2 139/445 consolesless mfs enumeration
  Description: SMB/SMB2 139/445  enumeration without the need to run msfconsole
  Note: sourced from https://github.com/carlospolop/legion
  Command: 
  ```
  msfconsole -q -x 'use auxiliary/scanner/smb/smb_version; set RHOSTS {IP}; set RPORT 139; run; exit' && msfconsole -q -x 'use auxiliary/scanner/smb/smb2; set RHOSTS {IP}; set RPORT 139; run; exit' && msfconsole -q -x 'use auxiliary/scanner/smb/smb_version; set RHOSTS {IP}; set RPORT 445; run; exit' && msfconsole -q -x 'use auxiliary/scanner/smb/smb2; set RHOSTS {IP}; set RPORT 445; run; exit' 
  ```










