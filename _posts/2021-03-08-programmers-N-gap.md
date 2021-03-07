---
layout: post
title: '프로그래머스 레벨1 x만큼 간격이 있는 n개의 숫자'
subtitle: level1 'x만큼 간격이 있는 n개의 숫자'
categories: algorithm
tags: programmers algorithm
---

for loop을 사용하기 보다 고차함수를 사용해서 푸는 습관을 들이자!

---

문제설명도 간단하다.

> 함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

```js
문제 예시
x = 2
n = 5
answer = [2,4,6,8,10]
```

map을 사용해서 더 간단하게 풀었으면 좋았을텐데...라는 아쉬움이 남는 문제였다.

알고리즘을 풀면 항상 for loop과 push가 생각나는 건 왜 일까??

---

##### 소스코드

**내가 푼 답안**

```js
function solution(x, n) {
  const answer = [];
  for (let i = 1; i <= n; i++) {
    answer.push(x * i);
  }
  return answer;
}
```

**모범 답안**

```js
function solution(x, n) {
  return Array(n)
    .fill(x)
    .map((v, i) => (i + 1) * v);
}
```

프로그래머스 level1 - x만큼 간격이 있는 n개의 숫자
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12954)**
