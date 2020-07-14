---
title: 3. React LifeCycle
date: 2020-07-12 16:07:12
tags: React
---

# React Component Life Cycle
react component가 생성 ~ 삭제까지 이루어지는 순서
![react-life_cycle](https://miro.medium.com/max/1400/1*hSO--5BPT1K_YK6VqRy4vg.png)

## 1. 자바스크립트 내 **constructor** 단계
  - 생성자 메소드로서 component가 처음 만들어 질 때 실행.
  - 최초 component가 mount되기 전 실행.
  - 일반적인 실행 이벤트 : 
    1. this.state 로 state 값을 선언/초기화
    2. 각종 Event 처리 Binding
  ```js
  class Login extends React.Component {
    constructor(props) {
      super(props);
      
      this.state = {
        isLogin = true,
        userInfo = null
      };
      this.handleBtnClick = this.handleBtnClick.bind(this);
    }
  } 
  ```
    > **constructor 주의사항**
    > 1. constructor를 사용시, `super(props)`를 반드시 호출하여 this.props 를 정의해 주어야 한다. 버그가 발생할 수 있다.
    >   - super : 상속된 부모 class 호출
    > 2. constructor 내부에서 `setState` 등의 업데이트를 사용하면 안 된다. Mount되기전 state업데이는 바람직하지 않다.

## 2. **Mount** 단계
  - component가 DOM에 Mount될 때, 실행.
  1. **render**
    - class Component에 반드시 필요한 메소드
    - Component 결과물을 Return하는 메소드
      - JSX 를 반환해야 함
    ```js
    class Login extends Component {
      render(){
        return <div>Component Rendering</div>
      }

      //return된 Element들이 가상 DOM에 mount되고 실제 DOM에 업데이트 됨
    }
    ```
    > **render 주의사항**
    > 1. render 단계 또한 `setState` 사용하면 안된다. render단계에서 setState가 되면 업데이트가 무한대로 이루어진다.
    <br/>
  2. **componentDidMount**
    - component가 DOM에 mount 되자마자 직후에 실행
    - 일반적인 실행 이벤트 : 
      1. data fetch (`api 통신`, `setState` .. )
        > DOM에 mount가 되어 준비가 된 상태에서 data를 넣어야하기 때문에, compenetDidMount단계에서 data binding작업을 한다.
      2. DOM 초기화 작업
    ```js
      class Home extends React.Component {
        state = {
          isLoading : true
        }

        componentDidMount () {
           this.setState({ isLoading : false});
        }

        render(){
          return <div>
          {this.state.isLoading ? "loading..." : "welcome"}
          </div>
        }
      }
    ```

## 3. **Updating** 단계
  - component가 update 될때 (setState)
  1. **render**
    - render메소드 재실행 됨
  2. **componentDidUpdate**
    - componentDidMount처럼 업데이트가된 직후에 실행!

## 4. **UnMount** 단계
  - DOM에서 component가 제거될 떄
  1. **componentWillUnMount**
    - 구성 요소를 해제하거나 파기 한 후에 실행 됨
    - 일반적인 이벤트 : 
      1. 일반적으로 네트워크 요청, 이벤트 리스너, 더 이상 필요하지 않은 요소와 같은 남은 항목을 제거하는데 사용

---
> 💡 **React 생명주기** : Mount -> Update -> UnMount
---
