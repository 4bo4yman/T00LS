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


### 5. Upload files

```
curl -F "Filedata=@./shell.php http://fkdjfal.example.com 
```



الأمر اللي كتبته بيستخدم أداة curl لرفع ملف بإسم shell.php من جهازك إلى رابط محدد، هو http://fkdjfal.example.com. خليني أشرحلك التفاصيل:

    curl -F: هذا الجزء من الأمر بيحدد إنك عايز ترفع ملف باستخدام بروتوكول HTTP POST.
    "Filedata=@./shell.php": هنا، بتحدد الملف اللي عايز ترفعه. @./shell.php يعني إن الملف موجود في نفس الدليل اللي انت فيه حالياً واسمه shell.php. Filedata هو اسم الحقل (field) اللي الملف حيروح فيه، وده بيكون حسب اللي السيرفر بيحتاجه.
    http://fkdjfal.example.com: ده عنوان السيرفر أو الرابط اللي حترفع الملف عليه.

بمعنى آخر، الأمر بيقول لـ curl: "ارفع لي الملف shell.php إلى السيرفر الموجود على الرابط http://fkdjfal.example.com باستخدام حقل البيانات Filedata".
