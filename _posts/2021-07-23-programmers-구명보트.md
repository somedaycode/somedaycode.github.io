---
layout: post
title: '프로그래머스 레벨2 구명보트'
subtitle: level2 '구명보트'
categories: algorithm
tags: programmers algorithm
---

효율성을 위해 시간복잡도를 생각하며 풀어야한다.

---

**문제 설명**

무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 2명씩 밖에 탈 수 없고, 무게 제한도 있습니다.

예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.

구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.

사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.

입출력 예
|people|limit|return|
|------|-----|-----:|
|[70, 50, 80, 50]| 100| 3|
|[70, 80, 50]| 100| 3|

---

**첫 시도**

정확성 테스트는 모두 통과했다.

하지만 효율성에서 빵점!

1. 사람들의 몸무게를 내림차순으로 정리한다.
2. 사람을 다 태울때까지 구명보트에 몸무게가 큰 순서대로 태우며 구명보트 개수를 1씩 늘린다.
3. 남은 사람들 중 `limit`에 걸리지 않을 가장 큰 몸무게의 사람을 찾고, `slice`를 이용해 남은 사람을 추려낸다.
4. 반복

for loop 안에서 slice를 사용해버려서 총 시간복잡도가 `O(n^3)`가 되어버렸다...

```javascript
function solution(people, limit) {
  let sorted = people.sort((a, b) => b - a);
  let answer = 0;
  while (sorted.length) {
    const top = sorted.pop();
    answer++;
    for (let i = 0; i < sorted.length; i++) {
      if (sorted[i] + top <= limit) {
        const a = sorted.slice(0, i);
        const b = sorted.slice(i + 1);
        sorted = a.concat(b);
        break;
      }
    }
  }
  return answer;
}
```

**두번째 시도**

코드는 조금 길어졌지만, 두번째 시도에서 효율성까지 통과하며 `O(n^2)`으로 끝냈다.

그런데 뭔가 복잡하다. 첫번째로 제출했던 코드를 좀만 수정하면 될 것같다.

```js
function solution(people, limit) {
  const peopleSet = {};
  let answer = 0;
  const p = people.sort((a, b) => b - a);

  for (let i = 0; i < p.length; i++) {
    if (!peopleSet[p[i]]) {
      peopleSet[p[i]] = 1;
    } else peopleSet[p[i]] += 1;
  }
  const keys = Object.keys(peopleSet);

  for (let i = 0; i < people.length; i++) {
    if (peopleSet[people[i]] === 0) continue;
    answer++;
    peopleSet[people[i]]--;
    for (let j = 0; j < keys.length; j++) {
      if (peopleSet[keys[j]] === 0) continue;
      if (Number(keys[j]) + people[i] <= limit) {
        peopleSet[keys[j]]--;
        break;
      }
    }
  }
  return answer;
}
```

---

**리팩토링 코드**

간단했던 걸 너무 어렵게 짜버렸던 것 같다.

처음에 접근했던 방식에서 불필요한 while문을 삭제했다.

큰 사람부터 순서대로 넣으면서 맨 끝에 있는 작은 사람과 더하여 limit에 걸리는지만 확인하면 되었던 것!

sort로 인해 `O(n log n)`

> V8 에서 javascript의 sort는 배열이 가지고 있는 원소 개수에 따라 시간복잡도가 달라진다. 10개 이하면 n^2

```js
function solution(people, limit) {
  let sorted = people.sort((a, b) => b - a);
  let answer = 0;

  for (let i = 0; i < sorted.length; i++) {
    answer++;
    const big = sorted[i];
    const small = sorted[sorted.length - 1];
    if (big + small <= limit) sorted.pop();
  }
  return answer;
}
```

---

프로그래머스 level2 - 구명보트

**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/42885)**
