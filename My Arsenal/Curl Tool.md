<h1>$${\color{blue}Curl}\space {\color{blue}tool }$$</h1>


### 1. GET Method: For display code source of domain if status code is 200
```
curl -X GET Domain.com
```

### 2. HEAD Method: For display header request only.
```
curl -I Domain.com
```

![image](https://github.com/4bo4yman/T00LS/assets/156849852/ed1aa551-b177-4949-97ba-e6a281185598)


### 3. OPTIONS Method: For display available methods with the request.
```
curl -X OPTIONS Domain.com -V
```



### 4. POST Method: For POST request such as login.
```
curl -X POST Domain.com/login.php
```

> login with username and password using curl

```
curl -X POST -d "name=admin&password=admin" Domain.com/login.php
```
