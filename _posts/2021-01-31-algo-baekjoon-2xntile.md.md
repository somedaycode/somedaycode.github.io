---
layout: post
title: '백준 11726 2xn Tile'
subtitle: 2xnTile
categories: Algorithm
tags: baekjoon,algorithm
comments: true
---

baekjoon 11726

[페이지이동](https://www.acmicpc.net/problem/11726)

## 2xn 타일링

**문제**

2×n 크기의 직사각형을 1×2, 2×1 타일로 채우는 방법의 수를 구하는 프로그램을 작성하시오.

아래 그림은 2×5 크기의 직사각형을 채운 한 가지 방법의 예이다.

**INPUT**
첫째 줄에 n이 주어진다. (1 ≤ n ≤ 1,000)

**OUTPUT**
첫째 줄에 2×n 크기의 직사각형을 채우는 방법의 수를 10,007로 나눈 나머지를 출력한다.

**예시**

```
INPUT OUTPUT
2     2

INPUT OUTPUT
9     55
```

**소스코드**

```js
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

rl.on('line', function (line) {
  const input = [];
  input.push(line);
  const dp = [0, 1, 2];
  const n = input[0];
  for (let i = 3; i <= n; i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
    dp[i] = dp[i] % 10007;
  }
  console.log(dp[n]);
}).on('close', function () {
  process.exit();
});
```

---

**설명**

DP 문제

```
2x1 은 타일이 1개
2x2 는 타일이 2개
2x3 은 타일이 3개
2x4 는 타일이 5개

2x5까지 그려서 확인을 해보니 8개가 나왔다.

dp[n] = dp[n-1] + dp[n-2]과 같음을 확인할 수 있었다.

```

> **침고사항**
> JS는 큰 수가 지원되지 않기 떄문에 10007을 나눈 나머지를 구하기 위해서는 반복문안에서 10007을 나누고 나머지 값을 배열에 집어 넣어야한다.

**틀린 답**

```js
// 이렇게 하면 `틀렸습니다`가 나온다.
for (let i = 3; i <= n; i++) {
  dp[i] = dp[i - 1] + dp[i - 2];
  dp[i] = dp[i];
}

// 나머지를 반복문 안에 넣어야함
// 너무 큰 수라 문제였던것
console.log(dp[n] % 10007);
```

**맞는 답**

```js
for (let i = 3; i <= n; i++) {
  dp[i] = dp[i - 1] + dp[i - 2];
  dp[i] = dp[i] % 10007; // 나머지를 반복문안에서 해결
}
console.log(dp[n]);
```
