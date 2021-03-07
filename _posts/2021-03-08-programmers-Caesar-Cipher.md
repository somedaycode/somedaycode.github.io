---
layout: post
title: '프로그래머스 레벨1 시저암호'
subtitle: level1 '시저암호'
categories: algorithm
tags: programmers algorithm
---

코드가 길어질 수 밖에 없는 문제라고 생각하지만... 내껀 알아보기도 힘들고, 완전 스파게티가 되버렸다.

---

아스키코드를 외우지는 못해도 어느정도는 알고있어야 문제를 풀 수 있다.

- 32는 공백

- 65 ~ 90은 대문자 알파벳

- 97 ~ 122은 소문자 알파벳

- 참고: 알파벳 개수는 총 26개이다.

---

##### 소스코드

**내 답안**

통과는 했지만, 너무 복잡하다.

이게 바로 스파게티 코드일까?

처음에 주어지는 테스트케이스는 모두 통과했지만, 제출 후 채점하기를 눌렀을 때는 모든 테스트케이스에서 실패했다.

문제는 n이 25를 받았을 때 소문자 혹은 대문자 알파벳의 아스키코드 범위를 훌쩍 넘어버리기 때문이였다.

단순히 z에서 1을 받았을 때, a로 넘어가기 위한 조건만을 생각해야하는 것이 아니였다.

나는 문제를 풀 때 너무 단순하게 생각하는 경향이 있는 것 같다.

주어지는 테스트케이스만을 생각하지 말자!

```js
function solution(s, n) {
  let aschi = [];
  for (let i = 0; i < s.length; i++) {
    let num = n;
    if (s.charCodeAt(i) === 32) {
      aschi.push(s.charCodeAt(i));
    } else if (s.charCodeAt(i) + num >= 122) {
      num = s.charCodeAt(i) + num - 122;
      if (num === 0) aschi.push(122);
      else aschi.push(97 + num - 1);
    } else if (s.charCodeAt(i) + num >= 90 && s.charCodeAt(i) < 97) {
      num = s.charCodeAt(i) + num - 90;
      if (num === 0) aschi.push(90);
      else aschi.push(65 + num - 1);
    } else aschi.push(s.charCodeAt(i) + num);
  }
  const answer = aschi.reduce((prev, asc) => {
    return prev + String.fromCharCode(Number(asc));
  }, '');
  return answer;
}
```

**내가 생각하는 모범답안**

이게 최고의 답안은 아닐지 모르지만, 아스키코드를 쓰지 않고 깔끔하게 코드를 작성하여 가독성을 높혔다고 생각한다.

```js
function solution(s, n) {
  const upper = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  const lower = 'abcdefghijklmnopqrstuvwxyz';
  let answer = '';

  for (let i = 0; i < s.length; i++) {
    let text = s[i];
    if (text === ' ') {
      answer += ' ';
      continue;
    }
    let textArr = upper.includes(text) ? upper : lower;
    let index = textArr.indexOf(text) + n;
    if (index >= textArr.length) index -= textArr.length;
    answer += textArr[index];
  }
  return answer;
}
```

프로그래머스 level1 - 직사각형 별찍기
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12926)**
