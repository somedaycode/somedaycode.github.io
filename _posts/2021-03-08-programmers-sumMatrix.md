---
layout: post
title: '프로그래머스 레벨1 행렬의 덧셈'
subtitle: level1 '행렬의 덧셈'
categories: algorithm
tags: programmers algorithm
---

이번 문제도 고차함수를 이용했으면 더 좋았을 문제... 아쉬움이 남는다.

---

**문제설명**

> 행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

```js
arr1	        arr2        	return
[[1,2],[2,3]]	[[3,4],[5,6]]	[[4,6],[7,9]]
```

"문제를 보자마자 forEach나 map을 사용하면 금방 풀겠는데?"
라는 생각과는 달리 배열 안의 배열, 그리고 배열끼리의 덧셈을 생각하니 뭔가.. 머리가 잘 굴러가지 않았다.

프로젝트를 할 때는 map, reduce와 같은 고차함수를 (그래도) 잘 사용하는데,

알고리즘 문제에서는 사용이 익숙치가 않다.

모범답안을 보면 저렇게 간단한데...

발상의 전환(?) 생각의 전환(?) 아무튼 그런게 필요한 시기인거 같다.

---

##### 소스코드

**내가 푼 답안**

```js
function solution(arr1, arr2) {
  const answer = [];
  let temp = [];
  for (let i = 0; i < arr1.length; i++) {
    for (let j = 0; j < arr1[i].length; j++) {
      temp.push(arr1[i][j] + arr2[i][j]);
    }
    answer.push(temp);
    temp = [];
  }
  return answer;
}
```

**모범 답안**

```js
function solution(arr1, arr2) {
  return arr1.map((a, i) => a.map((b, i2) => (b += arr2[i][i2])));
}
```

프로그래머스 level1 - 행렬의 덧셈
**[페이지 이동](https://programmers.co.kr/learn/courses/30/lessons/12950)**
