---
layout: post
title: '프로그래머스 레벨2 다리를 지나는 트럭'
subtitle: 레벨2 다리를 지나는 트럭
categories: algorithm
tags: programmers algorithm
---

큐를 사용해서 풀어야한다는 것은 알고 있었지만, 어떻게 코드로 풀어내야 할지 잘 모르겠어서 다른 사람들의 답안을 좀 참고했다.

bridge 배열에 0을 채우고 `shift`를 통해 빼주며 시간을 1씩 늘리는 것을 처음 풀 때 생각해냈으면 더 좋았을텐데 너무 아쉽다.

간단한 스택이나 큐 문제는 잘 푸는 것 같은데, 조금만 응용하는 문제가 나오면 감이 잘 안오는게 문제다.

스택과 큐를 이용해서 풀어야한다는 것을 깨닫는 순간부터 빈배열을 만들거나 기존에 주어지는 배열을 이용해서 풀려고하는 습관이 있는 것 같다.

이번 문제를 통해서 스택이나 큐가 항상 빈 상태로 존재하지 않아도 된다는 것을 깨달았다.

0을 채워놓고 다리를 관리하다니... 신박하다.

왜 이걸 생각못했지!!??!

**코드**

```js
function solution(bridge_length, weight, truck_weights) {
  const bridge = Array(bridge_length).fill(0);
  let second = 0;
  while (bridge.length) {
    bridge.shift();
    second++;

    if (truck_weights.length) {
      const sum = bridge.reduce((prev, curr) => prev + curr, 0);
      if (truck_weights[0] + sum <= weight) {
        bridge.push(truck_weights.shift());
      } else bridge.push(0);
    }
  }
  return second;
}
```

---

프로그래머스 level2 - 다리를 지나는 트럭

**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/42583)**
