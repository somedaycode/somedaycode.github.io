---
layout: post
title: '연결리스트 (Linked List)'
subtitle:
categories: develop
tags: document datastructure algorithm
---

어려운 개념이였던 연결리스트, 구현은 쉽지 않았다.

# 자료구조와 알고리즘

> 자료구조가 추구하고자 하는 목적은 메모리의 효율적 사용이다.

## 연결 리스트 (Linked List)

### Linked List

배열과 반대로, `추가, 삭제`가 빠르고 `검색`이 느리다.

- 각각의 데이터들이 흩어져있다. 그렇지만 연결되어있다.

- 배열과 같이 차례대로 저장하지만 그저 나열된 상태일 뿐 메모리에 연속적으로 위치하는 것이 아니다.

여러 노드들이 한 방향을 가리키고 있는 연결 구조이다

```js
첫 노드                                             마지막 노드
 ---- --     ---- --     ---- --      ---- --      ---- --
|head|  |-> |next|  |-> |next|  | -> |next|  | -> |tail|  |
 ---- --     ---- --     ---- --      ---- --      ---- --

 // head.next = node
 //마지막 노드가 가르키는 주소는 null
```

추가 또는 삭제가 일어날 때

```js

// 그림과 같이 node가 가리키는 방향만 달라지기 때문에 추가 또는 삭제가 빠르다.

fisrt node                                         last node
 ---- --     ---- --     ---- --      ---- --      ---- --
|head|  |-> |next|  |-> |next|  | -> |next|  | -> |tail|  |
 ---- --     ---- --     ---- --      ---- --      ---- --
                    \         /
                     ---- --
                    |new |  |
                     ---- --

 // head.next = node
 // the list terminates with a node pointing at `null`
```

#### 코드를 살펴보자

```py
class Node {
  constructor(data, next = null) {
    this.data = data,
    this.next = next;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
  }
}

```

LinkedList class의 인스턴스를 만들어보자

```js

`head`라는 프로퍼티를 가진 `list` 객체가 만들어졌다.

현재 `head(처음의 노드)`는 `null`을 가르킨다.
const list = new LinkedList();
```

---

#### 단순 연결 리스트 (singly Linked List)에 node를 추가하려면?

추가 작업은 3가지 상황에서 일어날 수 있다.

- head 앞에 추가

```js
// Linked class 내부에 메소드(함수)를 만든다
function addAtBegin(data) {
  // data와 next 값이 `null`인 newNode 객체를 만든다.
  let newNode = new Node(data);

  // newNode의 next 포인터는 head를 가르킨다
  newNode.next = this.head;

  // 첫번째 node, 즉 head가 newNode가 되면서 멘앞에 추가된다.
  this.head = newNode;
  return this.head;
}
```

- tail 뒤에 추가 (즉, list 마지막에 추가)

- 중간에 추가

`참조`
| 더 자세한 사항은 [Linked Lists in JavaScript (ES6 code)](https://codeburst.io/linked-lists-in-javascript-es6-code-part-1-6dd349c3dcc3) 참고

---

### 이중 연결 리스트 (Doubly linked list)

> 노드와 노드가 서로 연결되어 있다.
> 단순 연결 리스트와는 다르게 노드가 이전 노드(previous)와 다음 노드(next)로 구성되어있다.

```js
첫 노드                                             마지막 노드
 ----------      -----------       ------------       ------------
|  |head|  | <-> |  |next|  | <->  |  |next|  |  <->  |  |tail|  |
 ----------      -----------       ------------       ------------


// head.prev = `null`
// tail.next = `null`
```

#### 장점

- 단일로 이루어진 연결 리스트에 비해 더 효율적인 탐색이 가능하다.
- 양방향 탐색이 가능하다.

특히 이중 연결리스트는 node의 previous를 탐색하므로써 더 빠른 탐색이 가능하다. <br>
하지만 포인터를 2배 더 많이 사용하고 구현이 조금 더 복잡하다.

> 그러나 빠른 탐색으로 가지는 장점이 메모리가 늘어나는 단점을 상회한다.

---

### 원형 연결 리스트 (Circular linked list)

> tail이 가르키는 data가 head이다.

```js
첫 노드                                             마지막 노드
 ---- --     ---- --     ---- --      ---- --      ---- --
|head|  |-> |next|  |-> |next|  | -> |next|  | -> |tail|  |
 ---- --     ---- --     ---- --      ---- --      ---- --
      ^                                                 |
      |                                                 |
      ---------------------------------------------------


// head.prev = `null`
// tail.next = `null`
```

### 이중 원형 연결 리스트 (Circular doubly linked list)

> 말 그대로 위에서 본 이중 연결 리스트와 원형 연결 리스트를 합친 것이다

```js
첫 노드                                             마지막 노드
 ----------      -----------       ------------       ------------
|  |head|  | <-> |  |next|  | <->  |  |next|  |  <->  |  |tail|  |
 ----------      -----------       ------------       ------------
  ^                                                             ^
  |                                                             |
  ---------------------------------------------------------------


// head.prev = tail.next
// tail.next = head.prev

```

#### 장점

- 한 노드에서 모든 노드의 접근이 가능해져, 추가 및 삭제가 단순해진다.
- tail에 head를 연결해주는 코드로 연산 비용이나 코드량으로 보았을 때, 효율적인 자료구조가 가능해진다.
- 반복적인 순회가 일어날 때, 리스트의 끝을 확인할 필요가 없다.
