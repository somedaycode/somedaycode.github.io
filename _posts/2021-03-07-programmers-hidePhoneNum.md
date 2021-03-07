---
layout: post
title: '프로그래머스 레벨1 핸드폰 번호 가리기'
subtitle: level1 'hide-Phone-Number'
categories: algorithm
tags: programmers algorithm
---

쉬운 문제를 너무 어렵게 생각해서 푸는게 아닌가? 그런 생각이 든다.

처음에는 정규표현식을 사용해서 뒷자리만 남기고 모두 `*`로 바꾸고 싶었는데...

어떤 정규식을 써야하는지 감이 안잡혀서 내 식대로 풀게 되었다.

---

이 문제는 단순히 뒤의 4자리를 남기고 모두 `*`로 바꾸는 문제이다.

나는 주어지는 인자값을 `split`을 사용한 후 반복문을 통해 `*`로 바꾸어 주었는데,

더 편한 방법이 있었다. 그건 `repeat`이다.

> 주어진 문자열을 횟수만큼 반복하여 새로운 문자열을 반환하는 메서드!

이 `repeat`과 `slice`를 사용한다면 더 깔끔한 코드가 작성된다.

알고리즘 답안을 제출해서 통과를 하는 것도 중요하지만 더 깔끔한 코드를 작성할 수 있도록 노력해야겠다.

**정규표현식을 사용하고 싶다면?**

`\d(?=\d{4})` 이렇게 사용하면 된다.

`\d`는 숫자를 의미

`(?=)`는 positive lookahead로 `?=` 뒤에 매치되는 문자를 제외한 앞의 문자들을 결과로 보여준다.

> `\d(?=px) -> 2px 중 2만 매칭
> \d(?=\d{4}) -> 12345678 -> 1234만 매칭

---

##### 소스코드

**내가 푼 답안**

```js
function solution(phone_number) {
  const arr = phone_number.split('');
  const len = phone_number.length - 4;
  for (let i = 0; i < len; i++) {
    arr[i] = '*';
  }
  return arr.join('');
}
```

**모범 답안**

```js
function solution(phone_number) {
  const answer = '*'.repeat(phone_number.length - 4) + phone_number.slice(-4);
  return answer;
}
```

**문자열을 사용한 답안**

```js
function solution(s) {
  //
  return s.replace(/\d(?=\d{4})/g, '*');
}
```

프로그래머스 level1 - 핸드폰 번호 가리기
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12948)**
