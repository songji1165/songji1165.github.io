---
title: Javascript async await (es8) Updating..
date: 2019-05-20 18:07:12
tags: javascript
---

# async await (es8)

> 1. <mark> 여러 promise의 동작을 동기스럽게 사용할 수 있게 하고, 어떠한 동작을 여러 promise의 그룹에서 간단하게 동작하게 하는 것 </mark>
> 2. 사용법이 간단하고, 직관적

<br>
## 1. async await과 Promise
- async 함수의 리턴 값은 resolve 된 Promise 객체, 혹은 reject 된 Promise 객체를 암묵적으로 리턴
- function 키워드 앞에 async만 붙여주면 되고 비동기로 처리되는 부분 앞에 await만 붙여주면 됩니다. 
다만, 몇 가지 주의할 점이 있다면 await 뒷부분이 반드시 promise 를 반환해야 한다는 것과 async function 자체도 promise 를 반환한다는 것
- await는 Promise와 함께 사용되어야 합니다. await를 사용하면 Promise가 종료 될 때까지 함수 실행이 일시 정지 됩니다. 그후 Promise가 종료 되면 함수 실행이 다시 진행 됩니다. await 사용하면 Promise에서 resolve 된 값을 반환 받게 됩니다. await의 Promise가 reject 되면, 예외가 발생됩니다.

```js
async function goWork(time1, timeStartWork) {
  const time2 = await wakeUp(time1);
  const time3 = await takeSubway(time2);
  const time4 = await takeOffSubway(time3);
  const arrivalTime = await arriveWork(time4);
  if (arrivalTime > timeStartWork) {
    fire();
  }
}
```

[참고 버미노트 https://beomy.tistory.com/45](https://beomy.tistory.com/45)
