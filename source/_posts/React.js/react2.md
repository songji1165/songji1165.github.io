---
title: 2. React Component
date: 2020-07-11 16:07:12
tags: React
---

# React Component

## 1. React Component
1. component : HTML을 반환하는 함수
2. react application 하나에 하나의 component만 rendering 가능하다.
   - 부모 component에 자식 component 추가하는 방식
   - 추가 component는 모두 **[App component]** 안에 넣기
3. **Function Component, Class Component** 두가지 방식이 있다.
4. **JSX 사용 권장!!**

```js
// function Component
function App() {
  const title = "hello";
  return <div className="app">{title}</div>;
}

// Class Compnent
class App extends React.Component {
  render() {
    const title = "hello";
    return <div className="app">{title}</div>;
  }
}
```

<br/>

## 2. Component 특징

1. JSX
2. Component Props
3. State

#### 1. JSX방식 Component 생성

- Return 될 HTML은 JSX방식으로 사용한다.
  > JSX : REACT에서만 사용하는 개념 (HTML + javascript)
  >
  > 1.  `<div class="a">` X
  >     `<div className="a">` O
  > 2.  `<label for="a">` X
  >     `<label htmlFor="a">` O
  > 3.  JSX문법 안에서 javascript를 사용하고 싶을 경우 : { } 사용하기

1. ./src/App.js : Function Component 생성

```js
import React from "react";

function App() {
  return <div className="App">Hello World</div>;
}

export default App;
```

2. ./src/index.js : virtual DOM 위치 선언 (component)

```js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));

// (X) App : 기본 js에서의 변수명 입력하듯이 하면 안됨
// (O) <App/> : [JSX] 방식 사용해야함 - JSX에서 태그는 꼭 닫아야 함 </>
```

<br/>

#### 2. Component Props

1.  component간의 data 공유가 가능하다.

- **단방향** : 부모 -> 자식 만 가능하다.

  ```js
  function Hello(props) {
    return <div>This is {props.name}</div>;
  }

  function App() {
    return <Hello name="react" />;
  }
  ```

2.  component는 유일해야 한다. 중복 X

- component 재활용시에 자주하는 실수
  => key 속성을 통해 고유의 component 값을 생성해준다.

  - key props는 하위 coponent로 값 전달 X

    ```js
    const arr = ["react", "vue"];

    function Hello(props) {
      return <div>This is {props.name}</div>;
    }

    function App() {
      return (
        <div>
          {arr.map((data, index) => (
            <Hello name={data} key={index} />
          ))}
        </div>
      );
    }
    ```

      <br/>

#### 3. State (동적인 data)

- **Class Component에서 State를 사용**할 수 있다.
- State는 Object이다.
- **SetState** : state 변경시 사용하는 method
  - STATE를 직접 변경하여도, Class Component의 **render method**는 refresh되지 않음
    => **setState Method를 통해 render Method를 refresh 함!** (변경된 state data를 재 redering하는 것)
  - setState를 통해 State를 값을 추가할 수 있다!

1. ./src/App.js : Class Component 생성

```js
//App Class는 react Class Component로부터 properties를 상속받음

class App extends React.Component {
  state = {
    count: 0,
  };

  handliClick = () => {
    //state data 변경은 setState 사용 !!
    this.setState((current) => ({ count: current.count + 1 }));
  };

  //class component의 render method를 virtual DOM rendering

  render() {
    return (
      <div>
        {this.state.count}
        <button onClick={this.handleClick}>click me</button>
      </div>
      //vue 클릭이벤트와 동일하게 react도 클릭이벤트를 갖고 있음. onClick
    );
  }
}
```

> state가 필요 없는 경우에는 굳이, Class Component를 사용하지 않는다..
>
> > **React Hook** 추가되면서 function Component에서도 state를 사용할 수 있다!
