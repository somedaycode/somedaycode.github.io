---
layout: post
title: '프로그래머스 레벨1 완주하지 못한 선수'
subtitle: level1 완주하지 못한 선수
categories: algorithm
tags: programmers algorithm
---

정확도 테스트는 통과했지만 효율성은 통과하지 못했다..

결국, 다른사람의 답변을 보았다 :(

**내가 제출한 코드**

```js
function solution(participant, completion) {
  for (let i = 0; i < participant.length; i += 1) {
    for (let j = 0; j < completion.length; j += 1) {
      if (completion[j] === participant[i]) {
        completion.splice(j, 1);
        participant.splice(i, 1);
        return solution(participant, completion);
      }
    }
  }
  const answer = participant.join('');
  return answer;
}
```

딱 봐도 뭔가 비효율적이지 않은가?

이중반복문에 재귀라니..

풀면서 잘못 생각했던게 하나 있었다.

완주하지 못한 선수가 다수라 생각했는데, 답은 1명만 나오는 것이였다.

문제를 잘 읽었어야 했는데..

> 많은 마라톤 선수들이 마라톤에 참여하였습니다. **단 한 명의 선수**를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

---

#### 효율성을 O(n)으로 낮추려면 반복문을 한번만 쓰면된다.

어떻게?

sort를 이용하면된다.

```js
function solution(participant, completion) {
  let answer = '';
  participant.sort();
  completion.sort();
  for (var i = 0; i < participant.length; i += 1) {
    if (participant[i] !== completion[i]) {
      answer = participant[i];
      break;
    }
  }
  return answer;
}
```

#### 해시맵을 이용한 방법

다른사람의 코드를 참고했다.

아직 해시맵을 알고리즘 문제에 잘 적용하기가 어렵다.

더 많은 연습이 필요하다...

어떻게 이런 생각을 할 수 있는건지 나는 아직 놀라울 뿐 🙄

```js
function solution(participant, completion) {
  const runners = new Map();

  for (let i = 0; i < participant.length; i += 1) {
    let p = participant[i];
    let c = completion[i];

    // 처음 세팅값은 +1 또는 -1이 된다.
    map.set(p, (map.get(p) || 0) + 1);
    // 참여하면 value +1
    map.set(c, (map.get(c) || 0) - 1);
    // 완주했다면 value - 1 이로써 결국에 완주한 사람의 value는 0이 된다.
  }

  for (let [k, v] of runners) {
    if (v > 0) return k;
  }
}
```

---

프로그래머스 level1 - 완주하지 못한 선수
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/42576)**
