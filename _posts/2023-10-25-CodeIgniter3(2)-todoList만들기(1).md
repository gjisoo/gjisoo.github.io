---
title: "[CodeIgniter3] TodoList만들기(1)"
categories: [codeIgniter3]
tags:
    [
        CodeIgniter3
    ]

date: 2023-10-25
last_modified_at: 2023-10-25
excerpt: CodeIgniter3 - TodoList 만들기(1)
---

## 데이터베이스 설정하기

### items 테이블

|Column|Type|
|---|---|
|id(PK)|bigint / auto_increment / NOT NULL|
|content|varchar(200) / NULL|
|created_on |DATE / NULL|
|due_date|DATE NULL|
|used|INT(1) / NOT NULL/  DEFAULT 1|

샘플 데이터도 추가한다.

INSERT INTO items(content, created_on, due_date) VALUES('코딩','2023-10-12','2023-10-13');

### application/config/database.php

모델을 이용하기위해 사용자, 비밀번호, HOST, 데이터베이스 명을 입력한다.

![화면 캡처 2023-10-25 172443](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/8f43bdf1-e9a1-42ec-a0c6-cae5ae131c7f)

<br/><br/>

## 목록 만들기

todo 컨트롤러를 생성하고 조회, 목록, 쓰기, 삭제 등의 액션을 제어하는 함수를 정의해야 한다.  

우선 샘플 데이터의 목록을 화면에 출력하는 목록 함수를 먼저 만든다.  

### todo/application/controllers/main.php


![화면 캡처 2023-10-25 172754](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/da91a217-751a-4fa5-9407-cde7877b583f)

<br/><br/>

### todo/application/models/todo_m.php

모델은 전적으로 데이터 부분을 담당한다.  

![화면 캡처 2023-10-25 173012](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/f99f6da1-b38c-453c-8cc6-ba4d7e24eab4)

<br/><br/>

### todo/application/views/todo/list_v.php

화면에 출력하는 부분이다.  

![화면 캡처 2023-10-25 173200](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/202f44b9-35a5-4cd5-b446-a2da361ad01d)
![화면 캡처 2023-10-25 173219](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/6be84229-862f-432d-9ca0-6b371d28a60f)

<br/><br/>

#### 위와 같이 작성 후, localhost/todo/index.php/main/lists/ 에 접속하면 확인 가능하다.