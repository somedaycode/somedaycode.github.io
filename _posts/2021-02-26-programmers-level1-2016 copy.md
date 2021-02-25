---
layout: post
title: '프로그래머스 레벨1 2016'
subtitle: level1 '2016'
categories: algorithm
tags: programmers algorithm
---

new Date()를 잘 알면 바로 풀 수 있는 문제

Date 메소드를 알고 있다면

```
new Date('year, month, day').getDay()

// return 값으로 숫자 (0~6)이 나온다/
// 차례대로 일 월 화 수 목 금 토
```

**소스코드**

```js
function solution(a, b) {
  const day = new Date(`2016, ${a}, ${b}`).getDay();
  const days = 'SUN,MON,TUE,WED,THU,FRI,SAT'.split(',');
  return days[day];
}
```

프로그래머스 level1 - 2016
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12901)**
