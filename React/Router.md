## Router

### 라운팅이란 ?

웹 애플리케이션에서 라우팅이라는 개념은 사용자가 요청한 URL에 따라 알맞는 페이지를 보여주는 것을 의미한다. 웹 애플리 케이션을 만들 때 프로젝트를 하나의 페이지로 구성할 수도 있고, 여러 페이지를 구성할 수도 있다. 리액트 라우터를 사용하면 손쉽게 리액트 라우터로 싱글 페이지 애플리케인션을 만들 수 있다.

### 리액트 라우터 사용하기

react-router-dom 뮤듈을 설치 한 후 사용하기

#### Route 특정 주소에 컴포넌트 연결하기

```
<Route path="주소규칙" component={보여주고싶은 컴포넌트}>
```

```
import React from 'react';
import { Route } from 'react-router-dom';
import About from './About;
import Home from './Home';

const App = () => {
  return (
    <>
      <Route path="/" exact={true} component={Home/>
      <Route path="/about" component={About} />
    </Route>
  );
};

export default App;
```

#### Link 누르면 다른 주소로 이동시키기

Licnk 컴포넌트는 클릭하면 다른 주소로 이동시키는 컴포넌트이다. 리액트 라우터를 사용할 땐 `<a href="...">...</a>` 대신 Link 컴포넌트를 사용해야한다. 그 이유는 a 태그의 기본적인 속성은 페이지를 이동시키면서 페이지를 아예 새로 불러오게 된다. 그렇게 되면서 리액트 앱이 지니고 있는 상태들도 초기화되고, 렌더링된 컴포넌트들도 모두 사라고 새로 렌더링 하게된다.

```
import React from 'react';
import { Route, Link } from 'react-router-dom';
import About from './About';
import Home from './Home';

const App = () => {
  return (
    <div>
      <ul>
        <li>
          <Link to="/">홈</Link>
        </li>
        <li>
          <Link to="/about">소개</Link>
        </li>
      </ul>
      <hr />
      <Route path="/" exact={true} component={Home/>
      <Route path="/about" component={About} />
    </div>
  );
};

export default App;
```
