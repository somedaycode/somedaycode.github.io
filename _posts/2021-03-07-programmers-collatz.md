---
layout: post
title: '프로그래머스 레벨1 콜라츠 추측'
subtitle: level1 '콜라츠 추측'
categories: algorithm
tags: programmers algorithm
---

아주 쉬운 문제지만 더 깔끔하게 풀 수 있지 않을까?

그런 생각이 들었다.

---

**문제**

```
1-1. 입력된 수가 짝수라면 2로 나눕니다.
1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다.
2. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다.

이 작업을 몇번 하는가?
```

문제를 보자마자 바로 풀 수 있었지만, 테스트 케이스 13에서 실패!

곰곰히 생각해보니 1을 인자로 받았을 때는 0을 return 해야 했다.

함수 맨 앞에 조건문을 추가해주니 해결되었다.

##### 소스코드

**내가 푼 답안**

```js
function solution(num) {
  // 1을 받았을 때는 나누고 곱할 필요가 없으므로 0을 return
  if (num === 1) return 0;

  let answer = 0;
  while (answer !== 500) {
    if (num % 2 === 0) {
      num = num / 2;
    } else num = num * 3 + 1;

    answer++;
    if (num === 1) return answer;
  }

  return answer === 1 ? answer : -1;
}
```

프로그래머스 level1 - 콜라츠 추측
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12943)**
