---
layout: post
title: '프로그래머스 레벨1 수박수박수'
subtitle: level1 수박수박수
categories: algorithm
tags: programmers algorithm
---

아주 단순하게 (혹은 무식하게) 풀었다.

##### 문제설명

길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

**소스코드**

```js
function solution(n) {
  const answer = [];
  for (let i = 1; i <= n; i += 1) {
    if (i % 2 === 0) answer.push('박');
    // 2의 배수이면,
    else answer.push('수');
  }
  return answer.join('');
}
```

프로그래머스 level1 - 수박수박수박수박수
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12922)**
