<h1>$${\color{red}Wordlists}$$</h1>



## Kali Linux Default Lists

Below you will find a useful list of wordlists that are installed on Kali Linux by default. This is as of the latest version at the time of writing which is 2020.3. Anything with a wildcard (*) character indicates there's more than one list that matches. Keep in mind, a lot of these can be interchanged between modes. For example, "dir" mode wordlists (such as ones from the dirbuster directory) will contain words like "admin", "index", "about", "events", etc. A lot of these could be subdomains as well. Give them a try with the different modes!

  * /usr/share/wordlists/dirbuster/directory-list-2.3-*.txt
  * /usr/share/wordlists/dirbuster/directory-list-1.0.txt
  * /usr/share/wordlists/dirb/big.txt
  * /usr/share/wordlists/dirb/common.txt
  * /usr/share/wordlists/dirb/small.txt
  * /usr/share/wordlists/dirb/extensions_common.txt - Useful for when fuzzing for files!

## Non-Standard Lists

In addition to the above, Daniel Miessler has created an amazing GitHub repo called [SecLists](https://github.com/danielmiessler/SecLists). It compiles many different lists used for many different things. The best part is, it's in apt! You can ```sudo apt install seclists``` and get the entire repo! We won't dive into any other lists as there are many. However, between what's installed by default on Kali and the SecLists repo, I doubt you'll need anything else.



<br>

******
if this content liked you, follow me [Here](https://github.com/4bo4yman) ;) :tada:
*****
