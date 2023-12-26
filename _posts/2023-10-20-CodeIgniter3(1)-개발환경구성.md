---
title: "[CodeIgniter3] 개발환경구성"
categories: [codeIgniter3]
tags:
    [
        CodeIgniter3
    ]

date: 2023-10-20
last_modified_at: 2023-10-20
excerpt: CodeIgniter3 개발환경 구성과 Hello World 출력
---

## CodeIgniter 개발 환경 구성

윈도우에서 PHP 개발 환경을 구성하려면 Apache, PHP, MySQL (APM)을 각각 설치하고 설정해야 하는데, XAMPP를 이용하면 APM을 한번에 설치하고 관리할 수 있다.  

XAMPP 페이지(https://www.apachefriends.org/index.html)  

> 위 사이트에 접속하여 XAMPP for Windows를 클릭하여 다운로드 한다.  

설치 과정 중 옵션은 전부다 선택하거나 아래화면과 같이 선택한다.  

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/70681dc5-ab6b-41b0-8ea7-27794ccab579)

<br/>

> 설치 완료 후, 다운로드받은 해당 폴더로 가서 xampp 폴더를 선택한다.  
> 폴더안에 xampp-control에서 apache를 실행 시켜준다.  

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/b067fd21-3f44-4e29-bdf0-48732ceabad4)

<br/>

### CodeIgniter 설치

CodeIgniter 웹 사이트 (http://www.codeigniter.com/download)에서 CodeIgniter3을 다운로드 받는다.  

> xampp/htdocs에 있는 XAMPP 파일을 모두 삭제한 뒤에 내려받은 파일의 압축을 풀고 해당 파일을 xampp/htdocs로 복사한다.  

웹 브라우저에서 localhost로 접속했을 때 아래와 같은 화면이 나오면 끝이다.  

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/d02d6913-c3d4-4298-b3b6-c2159f28ac61)

<br/>

## Hello World 페이지 만들기

> application/config/routes.php를 보면 아래와같은 코드를 확인 할 수 있다.  

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/d853b79b-6e25-4500-895a-a36f1c2e33f7)

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/e51a374b-4bbf-4b46-80d0-a4c03116fb66)

#### defined('BASEPATH')

PHP의 defined() 함수를 사용하여 "BASEPATH" 상수가 이미 정의되었는지 확인한다.

#### exit('No direct script access allowed')

만약 "BASEPATH" 상수가 정의되지 않았거나 false라면, 스크립트 실행을 중지하고 메시지 "No direct script access allowed"를 출력한 후 스크립트를 종료한다.  

이 코드 조각의 주요 목적은 보안과 웹 애플리케이션의 직접적인 스크립트 액세스를 방지하는 것이다. 웹 애플리케이션에서는 일반적으로 특정 진입점 (예: index.php)을 통해만 접근을 허용하고, 직접적인 스크립트 실행을 방지하여 보안을 강화한다.  

CodeIgniter3에서 라우팅을 설정하려면 해당 파일을 편집해야 한다.  

이 파일을 사용하여 URL 경로를 컨트롤러 및 메소드에 매핑할 수 있다.  
<br/>

### 기본 라우팅

CodeIgniter에서 기본적으로 사용되는 라우팅은 URL 경로와 컨트롤러/메소드를 일치시키는 것이다.   

예를 들어, URL 경로 "/controller/method"는 "Controller" 클래스의 "method" 메소드에 매핑된다.  

<br/>

### 컨트롤러와 메소드 설정

```php
$route['default_controller'] = 'welcome';
```

위의 코드는 기본적인 라우팅 규칙을 정의하는데 사용된다.  
웹 애플리케이션이 루트URL로 접근 했을 때 어떤 컨트롤러와 메소드를 호출할지 결정한다.  
기본적으로 CodeIgniter 애플리케이션을 시작하면 'default_controller'에 지정된 컨트롤러와 메소드가 자동으로 호출된다.  

'default_controller' 경로가 'welcome'컨트롤러로 매핑된다.

```php
$route['products'] = 'catalog/products';
```

위의 코드는 'products' 경로가 'Catalog' 컨트롤러의 'products'메소드에 매핑된다.

<br/>

### 매개변수를 사용한 라우팅

CodeIgniter에서는 동적 URL 매개변수를 사용하여 라우팅을 정의할 수 있다.  
예를들어, 제품 ID를 사용하여 제품 상세 정보 페이지로 이동할 때  

```php
$route['product/(:num)'] = 'catalog/product/$1';
```

위의 코드는 'product/123'과 같은 URL에서 'catalog/product/123'과 같은 메소드로 매핑한다.  

<br/>

### 라우팅 재매핑

라우팅 규칙을 다시 매핑하려면 다음과 같이 설정한다.

```php
$route['old-route'] = 'new-route';
```

예를 들어, 기존 경로를 새 경로로 다시 매핑하려면 위와 같이 설정한다.  

<br/>

### 라우트 정규표현식

CodeIgniter에서 정규표현식을 사용하여 고급 라우팅 규칙을 정의할 수 있다.  

```php
$route['(^[0-9].*)'] = 'pages/view/$1';
```

위의 코드는 숫자로 시작하는 모든 경로를 "pages/view/숫자" 메소드로 매핑한다.  

이러한 예는 일반적인 라우팅 구성에 관한 것이며, 프로젝트 요구사항에 따라 더 복잡한 라우팅 규칙을 설정할 수 있다.  

<br/>

> 다음 controllers 폴더에 Welcome.php 파일이 있다. (컨트롤러의 파일명은 대문자로 시작한다.)

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/ea8e3273-8963-479c-8614-7eec46d880f7)

<br/>

CodeIgniter의 주소체계는 http://호스트/컨트롤러/메서드로 되어있다.  
routes.php에서 default_controller를 welcome.php로 지정하여 컨트롤러명은 알 수 있는데 실행되는 메서드명은 알 수 없다.  

welcome 컨트롤러의 index메서드가 기본적으로 호출되기 떄문이다. 이것은 CodeIgniter의 규칙 중 하나이다.

```php
$this->load->view('welcome_message');
```

뷰 파일을 로딩하라는 의미이며 application/views/welcome_message.php 파일이 로딩된다.  

#### welcome_message.php

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/41196cd0-6679-4ed7-b165-9146f3467150)

위의 부분을 아래와 같이 수정한다.  

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/cd461df1-4f53-4ad3-a041-87726d0d0c1a)

수정후 다시 localhost를 확인해보면 변경된걸 알 수 있다.

![image](https://github.com/gjisoo/gjisoo.github.io/assets/103836040/902c7a14-e2f2-4112-9926-7026cd8d2a70)


