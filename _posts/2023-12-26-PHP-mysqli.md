---
title: "[PHP] mysqli"
categories: [php]
tags:
    [
        PHP, mysqli
    ]

date: 2023-12-26
last_modified_at: 2023-12-26
excerpt: mysqli 연결하기
---

## PHP MYSQLI 연결하기

```php
$hostName="default_host";
$DBuserName="default_user";
$dbName="default_db";
$userPassword="default_pw";

// error 발생 시에 출력
mysqli_report(MYSQLI_REPORT_ERROR | MYSQLI_REPORT_STRICT);
$mysqli = new mysqli($hostName, $DBuserName, $userPassword, $dbName) or die("db connect error");
$mysqli->query("set session character_set_connection=utf8;");
$mysqli->query("set session character_set_results=utf8;");
$mysqli->query("set session character_set_client=utf8;");
```