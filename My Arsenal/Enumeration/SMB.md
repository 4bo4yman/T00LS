<h1>$${\color{blue}SMB}$$</h1>

### What is SMB?

SMB - Server Message Block Protocol - is a client-server communication protocol used for sharing access to files, printers, serial ports and other resources on a network. 

Servers make file systems and other resources (printers, named pipes, APIs) available to clients on the network. Client computers may have their own hard disks, but they also want access to the shared file systems and printers on the servers.Clients connect to servers using TCP/IP.

### What runs SMB?

Microsoft Windows operating systems since Windows 95 have included client and server SMB protocol support. Samba, an open source server that supports the SMB protocol, was released for Unix systems.


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/7bab627f-ada3-44fc-af96-d2f468fee9ed" >
</p> 

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

Enum4linux is a tool used to enumerate SMB shares on both Windows and Linux systems. It is basically a wrapper around the tools in the Samba package and makes it easy to quickly extract information from the target pertaining to SMB. It's installed by default on Parrot and Kali, however if you need to install it, you can do so from the official [github](https://github.com/CiscoCXSecurity/enum4linux).

The syntax of Enum4Linux is nice and simple: "enum4linux [options] ip"

```
TAG            FUNCTION

-U             get userlist
-M             get machine list
-N             get namelist dump (different from -U and-M)
-S             get sharelist
-P             get password policy information
-G             get group and member list
-a             all of the above (full basic enumeration)
```

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

SMBClient

Because we're trying to access an SMB share, we need a client to access resources on servers. We will be using SMBClient because it's part of the default samba suite.
We can remotely access the SMB share using the syntax:

```smbclient //[IP]/[SHARE]```

```
Followed by the tags:

-U [name] : to specify the user

-p [port] : to specify the port
```

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

> Hint: Try login Anonymous user and no password like this next picture.
![image](https://github.com/4bo4yman/T00LS/assets/156849852/8e15eaff-b2d2-412b-8123-69a6ea2f2c86)


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










