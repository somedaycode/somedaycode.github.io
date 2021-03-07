---
layout: post
title: '프로그래머스 레벨1 직사각형 별 찍기'
subtitle: level1 '직사각형 별 찍기'
categories: algorithm
tags: programmers algorithm
---

표준입출력 문제였는데, 너무 복잡하게 생각했다. 표준입출력에 대해 정확하게 알아야겠다.

---

**문제설명**

> 이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다.
> 별(\*) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.

```js
입력
5 3

출력
*****
*****
*****
```

단순히 `console.log`를 3번 반복하면 되었는데 `\n`을 쓰고 난리났다.

표준입출력이 무엇인지 정확히 알아보자!

---

##### 소스코드

**내 답안**

```js
process.stdin.setEncoding('utf8');
process.stdin.on('data', (data) => {
  const n = data.split(' ');
  const a = Number(n[0]),
    b = Number(n[1]);
  let answer = ``;
  for (let i = 0; i < b; i++) {
    for (let j = 0; j < a; j++) {
      answer += '*';
    }
    answer += '\n';
  }
  console.log(answer);
});
```

**내가 생각하는 모범답안**

```js
process.stdin.setEncoding('utf8');
process.stdin.on('data', (data) => {
  const n = data.split(' ');
  const a = Number(n[0]),
    b = Number(n[1]);
  const row = '*'.repeat(a);
  for (let i = 0; i < b; i++) {
    console.log(row);
  }
});
```

프로그래머스 level1 - 직사각형 별찍기
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12969)**
