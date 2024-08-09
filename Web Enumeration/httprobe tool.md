<h1>$${\color{red}httprobe}\space {\color{red}Tool }$$</h1>

### Install

```
go install github.com/tomnomnom/httprobe@latest
```

----------- 

# Basic Usage

### httprobe accepts line-delimited domains on stdin:

```
cat recon/example/domains.txt
example.com
example.edu
example.net
```

```
cat recon/example/domains.txt | httprobe
http://example.com
http://example.net
http://example.edu
https://example.com
https://example.edu
https://example.net
```


## Extra Probes

#### By default httprobe checks for HTTP on port 80 and HTTPS on port 443. You can add additional probes with the ```-p flag``` by specifying a protocol and port pair:

```
cat domains.txt | httprobe -p http:81 -p https:8443
```

### Timeout

You can change the timeout by using the ```-t flag``` and specifying a timeout in milliseconds:

```
cat domains.txt | httprobe -t 20000
```

### Skipping Default Probes

#### If you don't want to probe for HTTP on port 80 or HTTPS on port 443, you can use the -s flag. You'll need to specify the probes you do want using the -p flag:

```
cat domains.txt | httprobe -s -p https:8443
```

### Prefer HTTPS

##### Sometimes you don't care about checking HTTP if HTTPS is working. You can do that with the --prefer-https flag:

```
cat domains.txt | httprobe --prefer-https
```
