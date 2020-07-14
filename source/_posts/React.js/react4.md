---
title: 1. React Router
date: 2020-07-13 16:07:12
tags: React
---

# react router

[라우터 (네비게이션) 소스참고](https://github.com/songji1165/react_movie_app)

## 1. **react-router-dom**

네비게이션을 만들어주는 패키지

1. `$ npm install react-router-dom`
2. 주요 속성

   1. **HashRouter** , BrowserRouter

      - `HashRouter` : #으로 router를 구분함
        => 다른 서버를 같이 사용할 경우 router구분하기 용이함!
      - HashRouter사용을 권장함!

      ```js
      //App.js
      import { HashRouter, Route } from "react-router-dom";
      //...

      function App() {
        return (
          <HashRouter>
            <Navigation />
            <Route path="/" exact={true} component={Home} />
            <Route path="/about" component={About} />
            <Route path="/movie/:id" component={MovieDetail} />
          </HashRouter>
        );
        //<HashRouter> 안에 <Route>component를 통해 router기능을 사용하게된다!
      }

      export default App;
      ```

   2. **Router**

      - 2가지 Prop 기능

        1. path 설정
        2. 해당 path에 연결될 component (렌더링할 component)

        ```js
        <Route path="/" exact={true} component={Home} />

        //exact :
        //  path가 겹치면 해당 component가 모두 렌더링된다. exact를 통해 정확한 path 렌더링만 하게 한다!
        ```

   3. **Link**

   - Link는 Router안에 있어야 기능을 할 수 있다.
   - 새로고침시키는 <a>태그 대신, react router `<Link>`사용을 하면 새로고침없이 화면전환이 됨. (component 전환)

     ```js
     //Navigation.js
     import { Link } from "react-router-dom";
     //...

     function Navigation() {
       //a 태그는 html을 새로고침한다
       //react에서 SPA로써 새로고침없이 화면전환만 원할 경우 => react-router-dom의 link 메소드 사용하기!
       return (
         <div className="navi">
           <Link to="/">Home</Link>
           <Link to="/about">About</Link>
         </div>
       );
     }

     export default Navigation;
     ```

     ```js
       <Link
           to={{
               pathname:`/movie/${id}`,
               state:{
                   id, year, title, summary, poster, genres
               }
           }}
       >
     ```

     > `<Link to={{}}>`에 속성을 object형식으로 추가할 수 있다.

   4. **redirect**

      - path에 대한 속성.
      - `this.props.history` : router 속성을 통해 경로 변경을 할 수 있다.
      - `this.props.location` : 현재 path를 알 수 있다.

      ```js
      class MovieDetail extends React.Component {
        componentDidMount() {
          const { history, location } = this.props;

          if (location.state === undefined) {
            history.push("/");
          }
        }

        //...
      }
      ```
