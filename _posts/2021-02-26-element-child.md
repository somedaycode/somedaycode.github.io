---
layout: post
title: '엘리먼트의 자식요소의 순서를 바꿔보자'
subtitle: changing order of child in element
categories: develop
tags: javascript HTML
---

어떻게 부모요소 안에 있는 자식들의 순서를 바꿀 수 있을까?

예를 들어 이러한 HTML 코드가 있다고 가정해보자.

```html
//index.html
<body>
  <div class="wrapper">
    <p>나는 첫번째입니다.</p>
    <p>나는 두번째입니다.</p>
    <p>나는 세번쨰입니다.</p>
  </div>
</body>
```

`div` 밑에 3개의 `p`태그가 있다.

이걸 화면에 출력하면 이렇게 나온다.

```
나는 첫번째입니다.

나는 두번째입니다.

나는 세번쨰입니다.
```

만약 `첫번째`를 가장 밑으로 옮기고 싶다면 어떻게 해야할까?

```html
<body>
  <div class="wrapper">
    <p>나는 첫번째입니다.</p>
    <p>나는 두번째입니다.</p>
    <p>나는 세번쨰입니다.</p>
  </div>
</body>
<script>
  const div = document.querySelector('.wrapper');
  div.appendChild(div.firstElementChild);

  /*
  아래의 코드는 순서를 바꿔주지 않는다.
  div.appendChild(div.firstChild)
*/
</script>
```

> div를 선택한 후 div의 첫번째 자식요소를 `appendChild`를 통해 추가해주면 첫번째 자식요소는 맨뒤로 가게된다.

**출력예시**

```
나는 두번째입니다.

나는 세번쨰입니다.

나는 첫번째입니다.
```

`div.firstChild`가 순서를 바꾸지 못하는 이유는 nodeType이 `3`이기 때문이다.

nodeType 1은 element Node
nodeType 3은 element의 text이다.

따라서 콘솔창에 값을 입력해보면,

```js
console.log(div.firstChild); // #text를 출력하며 node의 각 정보를 알 수 있다. 현재 textContent는 ""

console.log(div.firstElementChild); // <p>나는 첫번째 입니다.</p>
```

---

### `insertadjacentElement`

자식 요소의 순서를 바꾸는 법은 정말 다양하다

그 중 제일 직관적이고 빠르게 사용할 수 있는 `insertadjacentElement`
를 소개한다.

`insertadjacentElement`는 인자를 2개 받는다.
선택할 수 있는 요소는 총 4가지다.

```
targetElement.insertAdjacentElement(position, element);

// 각 postion 위치
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</p>
<!-- afterend -->
```

위의 코드를 `insertadjacentElement`를 사용해 위치를 바꾸어본다면 이렇게 바꿀 수 있다.

```js
const div = document.querySelector('.wrapper');
div.insertAdjacentElement('beforeend', div.firstElementChild);
```

---

아래 코드와 같이 바꾸면 결과는?

```js
const div = document.querySelector('.wrapper');
div.insertAdjacentElement('afterend', div.firstElementChild);
```

```html
<div class="wrapper">
  <p>나는 두번째입니다.</p>
  <p>나는 세번쨰입니다.</p>
</div>
<!--afterend로 div를 벗어난 자리에 추가된다.-->
<p>나는 첫번째입니다.</p>
```
