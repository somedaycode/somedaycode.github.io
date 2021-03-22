---
layout: post
title: '프로그래머스 레벨1 정수 제곱근 판별'
subtitle: level1 '정수 제곱근 판별'
categories: algorithm
tags: programmers algorithm
---

주어진 값이 정수인지 판별하는 메소드가 뭐였더라?

---

문제를 보고 엄청 쉽고 간단하다고 생각했는데, `Number.interger()`이 생각이 안나서 시간을 끌었다.

`Math.sqrt(n)`하면 자바스크립트는 실수를 반환해서 정수인지 한번 판별해줘야한다.

**문제 설명**

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

##### 소스코드

**내가 푼 답안**

```js
function solution(n) {
  const sqrtN = Math.sqrt(n);
  if (Number.isInteger(sqrtN)) {
    return (sqrtN + 1) ** 2;
  } else {
    return -1;
  }
}
```

프로그래머스 level1 -
정수 제곱근 판별

**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12934)**
