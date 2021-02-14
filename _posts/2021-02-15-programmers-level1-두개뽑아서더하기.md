---
layout: post
title: '프로그래머스 레벨1 두 개 뽑아서 더하기'
subtitle: level1 두 개 뽑아서 더하기
categories: algorithm
tags: programmers algorithm
---

나름 금방 풀었던 문제, `...new Set`의 활용

주어진 배열에서 모든 두 수의 합을 중복없이 출력하면 된다.

**소스코드**

```js
function solution(numbers) {
  const result = [];
  for (let i = 0; i < numbers.length - 1; i += 1) {
    for (let j = 1 + i; j < numbers.length; j += 1) {
      result.push(numbers[i] + numbers[j]);
    }
  }
  const answer = [...new Set(result)].sort((a, b) => a - b);
  return answer;
}
```

이중반복문을 통해 두 수의 합을 result 배열에 저장한 이후,

`...new Set`을 통해 중복을 제거함.

그 다음 `sort`를 이용해 오름차순으로 정렬

---

**sort 함수 설명**

```js
const answer = [2, 10000, 500, 4, 1];
// 단순히 sort()로 사용하면 ascii 순서로 정렬된다.
console.log(answer.sort()); // [ 1, 10000, 2, 4, 500 ]

// 오름차순
console.log(answer.sort((a, b) => a - b)); // [ 1, 2, 4, 500, 10000 ]

// 내림차순
console.log(answer.sort((a, b) => b - a)); // [ 10000, 500, 4, 2, 1 ]
```

프로그래머스 level1 - 두 개 뽑아서 더하기
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/68644?language=javascript)**
