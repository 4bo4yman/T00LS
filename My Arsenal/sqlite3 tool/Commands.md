<h1>$${\color{blue}sqlite3}\space {\color{blue}tool }$$</h1>


* Introduction :
The most common (and simplest) format of flat-file database is an sqlite database. These can be interacted with in most programming languages, and have a dedicated client for querying them on the command line. This client is called "sqlite3", and is installed by default on Kali.

To access it we use: 
```
sqlite3 <database-name>
```
<p align="center">
<img src="https://github.com/4bo4yman/Web-Application-Penetration-Testing/assets/156849852/2a9f8e93-46b0-459c-a235-9deebf5e31ed" >
</p> 

* We can see that there is an SQlite database in the current folder.
  ```sqlite3 <database-name>```:

<p align="center">
<img src="https://github.com/4bo4yman/Web-Application-Penetration-Testing/assets/156849852/b7338fa3-eabc-4c25-a405-c24fe4ec8f66" >
</p> 

* From here we can see the tables in the database by using the ```.tables``` command:

<p align="center">
<img src="https://github.com/4bo4yman/Web-Application-Penetration-Testing/assets/156849852/2a73c7b7-2661-4df7-b6bf-9554b08bea81" >
</p> 

* At this point we can dump all of the data from the table, but we won't necessarily know what each column means unless we look at the table information. First let's use ```PRAGMA table_info(customers);``` to see the table information, then we'll use ```SELECT FROM customers;``` to dump the information from the table:

<p align="center">
<img src="https://github.com/4bo4yman/Web-Application-Penetration-Testing/assets/156849852/9fdbb642-6e4d-4621-b1fe-652938d70b5d" >
</p> 


We can see from the table information that there are four columns: custID, custName, creditCard and password. You may notice that this matches up with the results. Take the first row:

```
0|Joy Paulson|4916 9012 2231 7905|5f4dcc3b5aa765d61d8327deb882cf99
```

We have the custID (0), the custName (Joy Paulson), the creditCard (4916 9012 2231 7905) and a password hash (5f4dcc3b5aa765d61d8327deb882cf99).

In the next task we'll look at cracking this hash.

<br>

******
if this content liked you, follow me [Here](https://github.com/4bo4yman) ;) :tada:
*****
