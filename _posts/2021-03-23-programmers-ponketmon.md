---
layout: post
title: '프로그래머스 레벨1 폰켓몬'
subtitle: level1 '폰켓몬'
categories: algorithm
tags: programmers algorithm
---

문제 설명을 읽는 시간이 문제를 푸는 시간보다 길었다.

가끔, 문제 설명이 너무 길어서 풀기도 전에 겁을 먹는 경우가 있다.

풀고보니 아무것도 아니였다. 겁먹지 말자.

---

##### 소스코드

**내가 푼 답안**

```js
function solution(nums) {
  const diffPonketmons = [...new Set(nums)];
  const max = nums.length / 2;
  if (max < diffPonketmons.length) return max;
  return diffPonketmons.length;
}
```

---

**설명**

각기 다른 종류의 폰켓몬을 배열에 담기 위해서 `[...new Set(numbs)]`를 사용하여 중복되는 값이 없게 만들었다.

인자로 들어오는 폰켓몬의 종류 번호 배열의 길이를 2로 나누어 `max`에 담는다.

왜냐하면 선택할 수 있는 폰켓몬 종류의 최댓값은 N/2이기 때문이다.
(문제 설명 참고)

각기 다른 종류의 폰켓몬 개수가 max값보다 크다면 max를 return한다.

- 모든 폰켓몬의 종류가 달라도 가져갈 수 있는 폰켓몬은 n/2 즉, max 값이다.

다른 종류의 폰켓몬 개수가 max값보다 작다면 diffPonketmons 값을 return 한다.

---

프로그래머스 level1 - 폰켓몬

**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/1845)**
