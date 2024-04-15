# Offline password cracking

We might find passwords or other credentials in databases. These are often hashed, so we need to first identify which hash it is and then try to crack it. The first step is to identify the hash-algorithm that was used to hash the password.

## Identify hash

There are generally speaking three pieces of data we can use to identify a hash.

  - The length of the hash
  - The character set
  - Any special characters

In order to identify a hash we can either use specialized tools that analyze the hash and then return a guess on which algorithm it is. An easier way is of course to just look in the documentation of the software where you found the hashes. It usually says in the documentation or the source code which type of hash is being used.

### In kali we can use:

```
hash-identifier 
hashid
```
### online identifier services:

[hash-identification](http://www.onlinehashcrack.com/hash-identification.php)

[hashes.com](https://hashes.com/en/decrypt/hash)

[hash_type_checker](https://md5hashing.net/hash_type_checker)

[Hash Analyzer](https://www.tunnelsup.com/hash-analyzer/)


## Cracking the hash

Okay so now we know what hash it is, let's get cracking.

If you want to try out the functionality of hashcat or john the ripper you can find example hashes here: 
1. [hashcat/sample-hashes](https://hashcat.net/wiki/doku.php?id=example_hashes).
2. [john/sample-hashes](http://openwall.info/wiki/john/sample-hashes).


### Hashcat

Look for the specific type of hash you want to crack in the list produced by the following command:

```
hashcat --help
```

My hash was a ```Apache md5```, so I will use the corresponding code for it, ```1600```

```-m 1600``` - code of hash

```-a 0``` - straight

```-o found.txt``` - where the cracked hash outputs

```"admin.hash"``` - the hash you want to crack.

```/usr/share/hashcat/rules/rockyou-30000.rule``` - the wordlist we use

```
hashcat -m 11 -a 0 -o found.txt admin.hash /usr/share/hashcat/rules/rockyou-30000.rule
```

### John the ripper

So this is how you usually crack passwords with john

```
john --wordlist=wordlist.txt dump.txt
```

If you do not find the password you can add the john-rules. Which add numbers and such things to each password.

```
john --rules --wordlist=wordlist.txt dump.txt
```

### Password wordlists.

```
john --wordlist=test.txt --stdout --rules:Jumbo >> mutilated.txt
```
```
crunch 10 10 -t ,%Curtains -o ./worlist.curtains
```

### Linux shadow password

First you need to combine the passwd file with the shadow file using the unshadow-program.

```
unshadow passwd-file.txt shadow-file.txt > unshadowed.txt
john --rules --wordlist=wordlist.txt unshadowed.txt
```

### Using Online Tools

1. [CyberChef](https://gchq.github.io/CyberChef/)

2. [Crackstation](https://crackstation.net/)

3. [Hashkiller](https://hashkiller.co.uk/)

4. [100L5](https://10015.io/tools/md5-encrypt-decrypt)

5. [Base64](https://www.base64decode.org/)















