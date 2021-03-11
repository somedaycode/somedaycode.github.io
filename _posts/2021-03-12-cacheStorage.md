---
layout: post
title: 'What is CacheStorage? - 캐시스토리지를 사용해보자'
subtitle: how to use CacheStorage
categories: develop
tags: javascript Client-side-storage
---

클라이언트 영역에서 개발을 하면 다양한 데이터를 가공하여 쓰게 된다.

사용자가 자주 사용하는 데이터, 혹은 자주 사용하게 될 데이터를 매번 다운받는 것은 비효율적인 일이다.

Client-side storage는 이러한 문제점들을 보완하고 사용자가 브라우저를 더 효율적으로 사용할 수 있도록 도와준다.

Client-side에서 데이터를 저장하기 위한 방법은 다음과 같다.

- cookies
- Web Storage, IndexedDB
- Cache API

이번 글에서는 **Cache API**가 무엇인지 다루어보고자 한다.

---

# Cache

앞서 Cache, CacheStroage를 살펴보기 전에 Cache는 무엇인가 살펴보자.

> Cache란 어떠한 데이터를 임시 저장하는 장소를 말한다.
> 원래의 서버에서 정보를 찾아오는 것이 아닌, Cache로부터 데이터를 가져온다.
> 이를 통해, 더 빠른 속도로 데이터에 접근할 수 있다.

Cache API는 **request**에 대한 **HTTP response**를 저장하기 위한 획기적인 방식의 클라이언트 저장소다.

- 네트워크 연결 없이도 정보를 사용할 수 있도록 해준다
- 주로 [Service Worker API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)와 사용됨
- 하지만, 꼭 그럴 필요는 없음

## How to Use

**시나리오**

1. 사용자가 매번 접근해야하는 데이터가 있다.

2. 그 데이터는 `fetch`를 통해 가져오면 항상 3초가 걸린다고 가정한다.

3. `fetch`를 하고 브라우저의 `CacheStorage`를 통해 받아온 데이터를 저장한다.

4. 추후에 같은 데이터를 받아오게 된다면, `CacheStorage`의 데이터를 가져온다.

### code wihtout using Cache

데이터는 [jsonplaceholder](https://jsonplaceholder.typicode.com/todos)를 활용했다.

아래의 코드는 데이터를 받아올 때 3초가 걸린다.

```js
const delay = (data, time) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(data), time);
  });
};

const main = async () => {
  // delay를 통해 3초 지연
  const URL = 'https://jsonplaceholder.typicode.com/todos/1';
  try {
    const data = await delay(fetch(URL), 3000);
    console.log(data);
  } catch (err) {
    alert(err);
  }
};

main();
```

- 시간은 setInterval로 체크 했다.

**3초 후에 받은 Response**
![data1](../assets/img/Develop/cacheStorage/data1.png)

---

### code with Cache

**CacheStorage**를 활용하여 수정을 해보자.

```js
const main = async () => {
  const URL = 'https://jsonplaceholder.typicode.com/todos/1';

  // test라는 cacheName을 생성
  const cacheStorage = await caches.open('test');
  // 주어진 request와 일치하는지 확인한다. (request object ot it can be a URL string)
  const responsedCache = await cacheStorage.match(URL);

  try {
    if (responsedCache) {
      console.log(responsedCache);
    } else {
      const res = await delay(fetch(URL), 3000);
      await cacheStorage.put(URL, res);
      console.log(res);
    }
  } catch (err) {
    alert(err);
  }
};

main();
```

위 코드를 살펴보면, cacheStorage와 responsedCache 모두 await을 사용한 것을 볼 수 있다.

**중요!! Cache, Cache Storages는 Promise를 반환한다!!**

`caches.match()`는 request와 일치하는 response를 반환해준다. 만약 일치하는 반환값이 없다면 `undefined`를 반환한다. (`promise resolves with undefined`)

---

#### Cache Stroage가 잘 사용되는지 확인해보자

개발자 도구에서 Application 탭을 누르면 다음과 같은 Cache 카테고리를 찾을 수 있다.

`test`라는 `cacheName`이 보인다.
`test`는 `caches.open('test')`를 통해 생성된 것

![cacheStorage](../assets/img/Develop/cacheStorage/cacheCategory.png)

Cache Storage 메인 화면을 보면 이렇게 response Data가 test라는 이름의 cache에 잘 담겨져 있는 것을 확인할 수 있다.

![saved](../assets/img/Develop/cacheStorage/saved.png)

**Cache Storage를 사용한 결과**

![cacheUsed](../assets/img/Develop/cacheStorage/cacheUsed.png)

`cacheStorage`에 같은 값이 있는 것을 참조하여 `fetch`를 하지 않고 바로 데이터를 가져오는 것을 확인할 수 있다.

물론 새로운 데이터를 받아온다면 3초가 걸리지만, 이후 같은 값을 가져온다면 캐시를 참조하게 된다.

---

##### 참조사항

- 만약, async await을 사용하지 않고 promise, then으로 사용한다면 유의해야할 점이 하나있다.

```js
// response는 한번만 다루어지기 때문에 clone을 해주어야한다.
// clone을 안하면 에러가 뜸
const main = () => {
  const URL = 'https://jsonplaceholder.typicode.com/todos/1';
  return fetch(URL).then(function (response) {
    // clone을 안하면,
    // TypeError: Failed to execute 'put' on 'Cache': Response body is already used

    let responseClone = response.clone();
    caches.open('v1').then(function (cache) {
      cache.put(URL, responseClone);
    });
    return response.json(); // response를 이미 이곳에서 사용을 하기 때문이다.
  });
};
```

- 위 글에서는 저장된 cache를 삭제하는 예제는 다루지 않았다.
- 도메인은 여러개의 이름이 지정된 Cache 객체를 가질 수 있다.
- CacheStroage를 사용하여 특정 이름을 지정하여 cache 객체를 가져오고 유지 관리 할 수 있다.

---

> **Reference**
>
> > [MDN: Cache](https://developer.mozilla.org/en-US/docs/Web/API/Cache) //
> > [MDN: Cliet-side storage](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Client-side_web_APIs/Client-side_storage) //
> > [MDN: cacheStorage](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage) //

```

```
