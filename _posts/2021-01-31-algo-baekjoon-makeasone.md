---
layout: post
title: '백준 1463 1로 만들기'
subtitle: 2xnTile
categories: algorithm
tags: baekjoon algorithm
---

baekjoon 1463

**[페이지 이동](https://www.acmicpc.net/problem/1463)**

## 1로 만들기

정수 X에 사용할 수 있는 연산은 다음과 같이 세 가지 이다.

1. X가 3으로 나누어 떨어지면, 3으로 나눈다.
2. X가 2로 나누어 떨어지면, 2로 나눈다.
3. 1을 뺀다.

정수 N이 주어졌을 때, 위와 같은 연산 세 개를 적절히 사용해서 1을 만들려고 한다. 연산을 사용하는 횟수의 최솟값을 출력하시오.

**INPUT**
첫째 줄에 1보다 크거나 같고, 106보다 작거나 같은 정수 N이 주어진다.
`10`

**OUTPUT**
첫째 줄에 연산을 하는 횟수의 최솟값을 출력한다.
`3`

**힌트**

10의 경우에 10 -> 9 -> 3 -> 1 로 3번 만에 만들 수 있다.

---

**소스코드**

```js
const readline = require('readline');
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

const input = [];
const dp = [0, 0, 1, 1];
rl.on('line', function (line) {
  input.push(line);
  const n = input[0];
  for (let i = 1; i <= n; i++) {
    dp[i] = dp[i - 1] + 1;
    if (i % 3 === 0) {
      dp[i] = Math.min(dp[i / 3] + 1, dp[i]);
    }
    if (i % 2 === 0) {
      dp[i] = Math.min(dp[i / 2] + 1, dp[i]);
    }
  }
  console.log(dp[n] - 1);
}).on('close', function () {
  process.exit();
});
```

**설명**

DP 문제

이 문제에는 규칙이 있다.

1은 빼거나 나누지 않음으로 `0`
2는 2로 나누어 몫이 1이 된다. `1`
3도 3으로 나누어 몫이 1이 된다. `1`

4를 1로 만들기 위해서는 어떨까?

```
4를 2로 나누면 몫이 2이다.
2를 또 2로 나누어 1이 된다. (뭔가 익숙하지 않은가?)
총 2번이 걸린다.
```

5를 살펴보자

```
5에서 1을 뺀다. 숫자는 4가 된다. (1번)
우리는 아까 4를 1로 만들기 위해서 총 2번이 걸린다는 것을 알고 있다.

그래서 총 3번이 된다.
```

이러한 연산을 통해 배열 안에 값을 계속 저장해 나가는 것이다.

```js
(1을 뺴는 경우) dp[n] = dp[n-1] +1
if (n % 2 ===0) dp[n] = dp[n/2] +1
if (n % 3 ===0) dp[n] = dp[n/2] +1

// -1을 먼저 계산해서 dp[n]과 다음 계산과 비교해 최소값을 집어 넣어주어야 한다.
```

### 참고

dp[1]일 때 연산이 없으므로 0이여야 하지만 1이 되는 것을 확인 할 수 있다.

마지막에 -1을 붙여주자.
