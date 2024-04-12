<h1>$${\color{blue}hydra}\space {\color{blue}tool }$$</h1>

# hydra

Hydra is a parallelized login cracker which supports numerous protocols to attack. It is very fast and flexible, and new modules are easy to add.

This tool makes it possible for researchers and security consultants to show how easy it would be to gain unauthorized access to a system remotely.

It supports: Cisco AAA, Cisco auth, Cisco enable, CVS, FTP, HTTP(S)-FORM-GET, HTTP(S)-FORM-POST, HTTP(S)-GET, HTTP(S)-HEAD, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MySQL, NNTP, Oracle Listener, Oracle SID, PC-Anywhere, PC-NFS, POP3, PostgreSQL, RDP, Rexec, Rlogin, Rsh, SIP, SMB(NT), SMTP, SMTP Enum, SNMP v1+v2+v3, SOCKS5, SSH (v1 and v2), SSHKEY, Subversion, Teamspeak (TS2), Telnet, VMware-Auth, VNC and XMPP.

Installed size: ```956 KB```

How to install: ```sudo apt install hydra```


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/ffd5bdea-2a41-4481-854f-c24a698deb41" >
</p> 

| Command | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| hydra -P password-file.txt -v $ip snmp                                                                                                    | Hydra brute force against SNMP                       |
| hydra -t 1 -l admin -P /usr/share/wordlists/rockyou.txt -vV $ip ftp                                                                       | Hydra FTP known user and rockyou password list       |
| hydra -v -V -u -L users.txt -P passwords.txt -t 1 -u $ip ssh                                                                              | Hydra SSH using list of users and passwords          |
| hydra -v -V -u -L users.txt -p "<known password>" -t 1 -u $ip ssh                                                                         | Hydra SSH using a known password and a username list |
| hydra $ip -s 22 ssh -l <user> -P big_wordlist.txt                                                                                         | Hydra SSH Against Known username on port 22          |
| hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f $ip pop3 -V                                                                          | Hydra POP3 Brute Force                               |
| hydra -P /usr/share/wordlistsnmap.lst $ip smtp -V                                                                                         | Hydra SMTP Brute Force                               |
| hydra -L ./webapp.txt -P ./webapp.txt $ip http-get /admin                                                                                 | Hydra attack http get 401 login with a dictionary    |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt rdp://$ip                                                           | Hydra attack Windows Remote Desktop with rockyou     |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt $ip smb                                                             | Hydra brute force SMB user with rockyou:             |
| hydra -l admin -P ./passwordlist.txt $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location' | Hydra brute force a Wordpress admin login            |
| hydra -L usernames.txt -P passwords.txt $ip smb -V -f | SMB Brute Forcing |
| hydra -L users.txt -P passwords.txt $ip ldap2 -V -f | LDAP Brute Forcing |

## hydra Usage Example
Attempt to login as the root user (```-l root```) using a password list (```-P /usr/share/wordlists/metasploit/unix_passwords.txt```) with 6 threads (```-t 6```) on the given SSH server (```ssh://192.168.1.123```):

EX:

```
hydra -l root -P /usr/share/wordlists/metasploit/unix_passwords.txt -t 6 ssh://192.168.1.123
```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/e1e9537c-e794-48d8-b2c2-9b9d21728402" >
</p> 

*********

<h1>$${\color{blue}pw-inspector}\space {\color{blue}tool }$$</h1>


ولنفترض عندنا قائمة كلمات بها الالاف من الكلمات ذات عدد حروف مختلفة ولكننا نعلم ان password تبعنا مكونة من اربع حروف فقط ؟! 
فلماذا لا نستخدم جميع الكلمات ذات الحدود 4 حروف فقط ؟ ذلك سيوفر علينا العديد من الوقت
لدينا اداة جديدة توفر لنا تلك المهمة وهي ```pw-inspector```

## pw-inspector Usage Example

Read in a list of passwords (```-i /usr/share/wordlists/nmap.lst```) and save to a file (```-o /root/passes.txt```), selecting passwords of a minimum length of 6 (```-m 6```) and a maximum length of 10 (```-M 10```):

EX:

```
pw-inspector -i /usr/share/wordlists/nmap.lst -o /root/passes.txt -m 6 -M 10
```
Practice:

![image](https://github.com/4bo4yman/T00LS/assets/156849852/28fe91e4-22f7-470f-8173-c78d45f70ad9)

![image](https://github.com/4bo4yman/T00LS/assets/156849852/1bd38f1f-7074-474d-b5e4-80532587cd5e)








