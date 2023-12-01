---
title: "[jquery] body no-scroll "
categories: [front-end]
tags:
    [
        front-end
    ]

date: 2023-12-01
last_modified_at: 2023-12-01
excerpt: body 스크롤 비활성화
---

## jquery, css body 스크롤 막기

팝업창이 뜰때 body 스크롤을 막아야 하는경우

### JQuery

```javascript

function openIdModal(){
	$('.userIdModal').css('display','block');
	$('body').addClass('no-scroll').on('scroll touchmove mousewheel', function(e){
		e.preventDefault();
	});
}

$(document).ready(function() {
    $('#confirmBtn').click(function() {
		$('body').removeClass('no-scroll').off('scroll touchmove mousewheel');
        $('.userIdModal').css('display', 'none'); // 모달 창 숨기기
    });
});

```

### CSS

```css
.no-scroll {
    height:100%; 
    min-height:100%; 
    overflow:hidden 
    !important; 
    touch-action:none;
}
```