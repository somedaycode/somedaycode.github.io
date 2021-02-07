---
layout: post
title: 'Map과 Object'
subtitle:
categories: develop
tags: document javascript map object
---

[Hello Coding 그림으로 개념을 이해하는 알고리즘](http://www.yes24.com/Product/Goods/37885448)을 읽으며 Map과 Object의 차이점이 뭘까? 라는 의문이 들었다.

위 책을 통해 해시 테이블이 무엇인지 대략적으로 알게 되었다.

해시 함수를 통해 key값을 알고 있다면, key값에 맞는 value를 아주 손쉽게 가져올 수 있다.

예를들어, 음식마다 칼로리의 양을 해시테이블에 저장해놓았다면, Food['pizza']를 통해 피자의 칼로리를 알 수 있다.

_아주 간략하게 설명했다._

여기서 의문이 생겼다. 이미 Object로 key와 value값을 지정하고 원하는 탐색을 할 수 있는데 Map은 무엇이 다를까?

ES6에서는 Map객체를 통해 key와 value값을 연결시켜 저장할 수 있다.
`Map.set, Map.delete, Map.get, Map.has`를 통해 손쉽게 값을 지정하고 지우고 가져오며 확인할 수 있다.

차이점은 다음과 같다.

- Object의 key값은 문자열(strings)이다.
- Map.size를 통해 크기를 쉽게 알 수 있다.
- Map은 넣은 순서대로 반복이 된다.

> [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map)에서는 모든 Key와 value의 타입이 일정하다면 Map을 사용하라는 팁이 쓰여져 있음을 확인할 수 있다.
