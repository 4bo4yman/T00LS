<h1>$${\color{red}httpx} \space {\color{red}Tool } $$</h1>


## HTTPX is an open source tool designed to facilitate inspections and interactions with applications and servers over the HTTP protocol. It is part of the ProjectDiscovery toolkit.


#### HTTPX features:

1. Security Check: Supports checking for TLS/SSL protocols.
2. Determine HTTP statuses: Can be used to verify HTTP response codes such as 200, 404, etc.
3. Services Scan: It can scan specific ports and determine which services are running on them.
4. Ease of use: Easy to integrate with other tools like Subfinder and Amass.


**How to install HTTPX:**

You can install HTTPX using the following command:



```
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

How to use HTTPX:
Basic use:

To check the HTTP status of a group of domains:


```
echo "example.com" | httpx
```

Or you can use a list of ranges from a file:

```
httpx -l targets.txt
```

### Advanced Options:

 ##### Save results to a file:

```
echo "example.com" | httpx -o results.txt
```


##### Make sure HTTPS is present:

```
echo "example.com" | httpx --tls-probe
```

###### Checking a specific HTTP status:

```
echo "example.com" | httpx --status-code
```

##### Use of input and output files:

```
httpx -l input.txt -o output.txt
```

###### Parallelism (number of threads):

```
echo "example.com" | httpx -c 50
```


###### Integrate HTTPX with other tools:

You can integrate HTTPX with tools like Subfinder to collect subdomains and check their status:

```
subfinder -d example.com -o subdomains.txt
cat subdomains.txt | httpx -o live_subdomains.txt
```


###### Practical example:

Let's say you want to check the HTTP status of subdomains you've collected using Subfinder:

 ###### Collect subdomains using Subfinder:

```
subfinder -d example.com -o subdomains.txt
```

Check the HTTP status of subdomains using HTTPX:

```
cat subdomains.txt | httpx -o live_subdomains.txt
```

### Filter only the ranges that give a status of 200 OK:

```
cat live_subdomains.txt | grep "200"
```


```
cat subdomains.txt | httpx -o live_subdomains.txt -status-code
```


```
cat subdomains.txt | httpx -o live_subdomains.txt -title
```

###### If there 302 redirection , we need open redirect:


```
cat subdomains.txt | httpx -o live_subdomains.txt -location
```

## Python script to use HTTPX with Subfinder:

If you prefer to use Python, you can write a script to use HTTPX with Subfinder:

```
import subprocess

# Run Subfinder
subfinder_command = "subfinder -d example.com -o subdomains.txt"
subprocess.run(subfinder_command, shell=True)

# Run HTTPX
httpx_command = "cat subdomains.txt | httpx -o live_subdomains.txt"
subprocess.run(httpx_command, shell=True)

# Filter for status 200 OK
with open('live_subdomains.txt', 'r') as file:
 lines = file.readlines()

for line in lines:
 if "200" in line:
 print(line.strip())
```

With this script you can collect subdomains and check their status quickly and easily
