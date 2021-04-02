---
layout: post
title: '프로그래머스 레벨2 가장 큰 수'
subtitle: level2 '가장 큰 수'
categories: algorithm
tags: programmers algorithm
---

정답 코드에 근접했지만 혼자 힘으로는 풀지 못했다. 조금 더 생각의 전환이 필요할듯

---

**문제 설명**

0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.

| numbers           |    return |
| ----------------- | --------: |
| [6, 10, 2]        |    "6210" |
| [3, 30, 34, 5, 9] | "9534330" |

---

**첫 시도**

내가 처음에 생각했던 방법은 다음과 같다.

1. 각 숫자를 `string`으로 변환한다.
2. 변환한 `string`값의 맨 첫 글자(number)를 가져온다.
3. 서로 비교하여 큰 숫자를 배열 맨 앞에 둔다.
4. 같다면 그 뒤의 숫자를 비교한다.

하지만 코드를 다음과 같이 짜니, 문제가 발생했다.

```javascript
// 탐색으로 맨 앞의 숫자를 기준으로 배열을 배치한다.
function solution(numbers) {
  for (let i = 0; i < numbers.length; i++) {
    let swap;
    for (let j = i + 1; j < numbers.length; j++) {
      let strA = String(numbers[i]).substring(0, 1);
      let strB = String(numbers[j]).substring(0, 1);
      if (strA > strB) break;
      if (strA === strB) {
        // 같으면..?
      }
      swap = numbers[i];
      numbers[i] = numbers[j];
      numbers[j] = swap;
    }
  }
  return numbers;
}
```

빼내온 값이 같을 때의 상황을 코드로 처리하자니 막막하고,

`30` 혹은 `3`을 비교할 때 `3`이 `30`보다 뒤에 있게 되었다.

> 330 > 303

그래서 다르게 생각을 해보았다.

`sort()` 혹은 `reduce`를 사용해보면 어떨까?

`sort`를 통해 값을 비교하고 출력하는 것 이다.

코드는 아래와 같이 작성했다.

**제출 코드**

```js
function solution(numbers) {
  const answer = numbers
    .map((number) => String(number))
    .sort((a, b) => b + a - (a + b));
  if (answer[0] === '0') return '0';
  return answer.join('');
}
```

아쉬운 점은 sort함수를 다 작성할 때 string으로 바꾼 값을 어떻게 비교를 해야할지 잘 몰라서 다른 분의 블로그를 참고하였다.

sort 함수 처리
`[6, 10, 2]` 일 때,

`sort`는 `b + a - (a + b)`이 부분을 통해 다음과 같이 동작한다.

| order | process | result |
| ----- | :-----: | ------ |
| 0     | 6 10 2  |        |
| 1     | 610 106 | 6 10   |
| 2     | 102 210 | 2 10   |

610과 106을 비교한 후 102와 210을 비교한다.

이런 비교를 통해 결국에는 이어붙인 수 중 큰 수가 앞에 오게된다.

또 다 작성한 후 마지막 테스트케이스를 통과하지 못했다.

이유는 배열 안이 모두 0 값일 때 따로 처리를 해주어야 한다.

---

프로그래머스 level2 - 가장 큰 수

**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/42746)**
