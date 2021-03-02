---
layout: post
title: '프로그래머스 레벨1 문자열 내 마음대로 정렬하기'
subtitle: level1 문자열 내 마음대로 정렬하기
categories: algorithm
tags: programmers algorithm
---

이 문제를 통해 `sort()`를 더 자세하게 알 수 있었다.

##### 문제설명

문자열로 구성된 리스트 strings와, 정수 n이 주어졌을 때, 각 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하려 합니다. 예를 들어 strings가 ["sun", "bed", "car"]이고 n이 1이면 각 단어의 인덱스 1의 문자 "u", "e", "a"로 strings를 정렬합니다.

내가 제출하여 통과한 **소스코드**

```js
function solution(strings, n) {
  return strings.sort((a, b) => {
    if (a[n] > b[n]) return 1;
    if (a[n] < b[n]) return -1;
    if (a[n] === b[n]) {
      if (a > b) return 1;
      if (a < b) return -1;
      if (a === b) return 0;
    }
  });
}
```

**내가 푼 코드 설명**

기존의 sort를 쓰면서 각 `string`의 `index`를 기준으로 정렬하면 된다.

같은 문자를 가진 경우에는 **사전을 기준으로 정렬**해야하니 조건문을 통해 전체 문자열을 비교하여 return을 하게 했다.

예를들어서, n이 2일때,
abce와 abcd는 c가 같으므로 abce와 abcd를 문자열 전체로 비교하게 되는 것이다.

---

가장 많은 추천을 받은 **소스코드**

```js
function solution(strings, n) {
  return strings.sort((s1, s2) =>
    s1[n] === s2[n] //
      ? s1.localeCompare(s2)
      : s1[n].localeCompare(s2[n])
  );
}
```

이 코드를 통해 `localeCompare`이 무엇인지 알게 되었다.

> String.prototype.localeCompare()
> 기존 문자열하고 비교하여 비교하는 문자열이 전,후 또는 같은 순서인지 알려주는 숫자를 리턴한다 - [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)

- 음수를 반환하면 비교하는 숫자가 뒤에 있는 것
- 양수를 반환하면 비교하는 숫자가 앞에 있는 것
- 0을 반환하면 같은 순서

헷갈릴 수 있는데, 비교하는 대상을 기준으로 잡고 생각하자.

```js
//음수를 반환, 그러므로 c가 a보다 뒤에 있다.
'a'.localeCompare('c');

// 양수를 반환, 그러므로 ago가 energy보다 앞에 있다.
'enegry'.localeCompare('ago');
```

프로그래머스 level1 - 문자열 내 마음대로 정렬하기
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12915)**
