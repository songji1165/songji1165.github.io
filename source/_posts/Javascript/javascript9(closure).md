# 클로저 Closure

- 함수형 프로그래밍 언어에서 사용되는 중요한 특성

- 클로저 : 함수가 선언 됬을 때의 **렉시컬환경**

> 렉시컬 스코핑(Lexical scoping)
> 스코프가 결정되는 범위를 말하며, `함수, 변수를 호출할 때가 아니라 함수, 변수를 어디에 선언하였는지에 따라 결정되는 것`

### 스코프체인과 렉시컬 스코프의 관계

```js
function outerFunc() {
  var inner = "local";

  function innerFunc() {
    console.log(inner);
  }
  innerFunc();
}

outerFunc();
// local
```

- innerFunc가 상위 스코프에 접근할 수 있는 것은 렉시컬스코프의 레퍼런스를 차례대로 저장하고 있기 때문이다.
