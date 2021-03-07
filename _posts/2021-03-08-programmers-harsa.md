---
layout: post
title: '프로그래머스 레벨1 하샤드 수'
subtitle: level1 '하샤드 수'
categories: algorithm
tags: programmers algorithm
---

문제를 다 풀고 리팩토링을 거치니 더 깔끔한 코드가 나와 기분이 좋다.

---

**문제설명**

> 양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

```js
입출력 예 #1
10의 모든 자릿수의 합은 1입니다. 10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.

입출력 예 #2
11의 모든 자릿수의 합은 2입니다. 11은 2로 나누어 떨어지지 않으므로 11는 하샤드 수가 아닙니다.
```

---

##### 소스코드

x를 문자열로 바꾼 후 split을 통해 배열로 바꾼다.
배열은 reduce를 통해 각 자릿수의 합을 리턴하게 된다.

**설명**

1. x는 11이다.
2. `toString()`과 `split('')`을 통해 [1,1]이 된다.
3. `reduce`를 통해 배열 안의 모든 값을 더해주고 2를 반환한다.
4. 11을 2로 나누었을 때 나머지는 0이 아니므로 false를 return 한다.

**리팩토링 후 코드**

```js
function solution(x) {
  const sum = x
    .toString()
    .split('')
    .reduce((prev, curr) => Number(prev) + Number(curr));
  return x % sum === 0 ? true : false;
}
```

**리팩토링 전 코드**

```js
function solution(x) {
  const num = x.toString().split('');
  let answer = true;
  let sum = 0;

  for (let i = 0; i < num.length; i++) {
    sum += Number(num[i]);
  }

  if (x % sum !== 0) answer = false;
  return answer;
}
```

프로그래머스 level1 - 하샤드 수
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12947)**
