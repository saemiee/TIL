## props

props는 properties의 약자로 어떠한 값을 컴포넌트에게 전달해야 할 때 props를 사용한다.

### props 기본 사용법

```
// App.js
import React from 'raact';
import Hello from './Hello';

const App = () => {
  return (
    <Hello name="react" />
  );
}

export default App;
```

```
// Hello.js
import React from 'react'

const Hello = (props) => {
  retrun <div>안녕 {props.name}</div>
}

export default Hello.;
```

컴포넌트에게 전달되는 props는 파라미터르 통하여 조회 할 수 있다. props는 객체 형태로 전달되며, 만약 `name` 값을 조회하고 싶다면 `props.nam`e 을 조회한다.

### props 비구조화 할당

```
// App.js
import React from 'react';
import Hello from './Hello`;

const App = () => {
  return (
    <Hello name="react" color="blue" />
  )
}


export default App;
```

```
import React from 'react;

const Hello = ({color, name}) => {
  retrun (
    <div styled={{ color }}>안녕 {name}</div>
  )
}

export default Hello;
```

함수의 파라미터에서 비구조화 할당 문법을 사용하면 더 간결한 코드를 작성 할 수 있다.

### defaultProps 기본값 설정

컴포넌트에 props 를 지정하지 않았을 때 기본적으로 사용할 값을 설정한다면 defaultProps 라는 값을 설정한다.

```
// App.js
import React from 'react';
import Hello from './Hello';

const App = () => {
  retrun (
    <Hello colo="pink">
  )
}

export default App;
```

```
// Hello.js
import React from 'react';

const Hello = ({color, name}) => {
  retrun (
    <div styled={{color}}>안녕 {name}</div>
  )
}

Hello.defaltProps = {
  name: '이름없음'
}

export default Hello;
```

### props.children

컴포넌트 태그 사이에 넣은 값을 조회하고 싶을 땐 `props.children` 을 조회한다.

```
// Wrapper.js
import React from 'react';

const Wrapper = ({ childern }) => {
  const style = {
    border: 2px solid #000000,
    padding: '16px',
  };
  return (
    <div style={style}>
      {children}
    </div>
  )
}

export default Wrapper;
```

```
// App.js
import React from 'react;
import Hello from './Hello';
import Wrapper from './Wrapper';

const App = () => {
  return(
    <Wrapper>
      <Hello name="saemi" color="pink"/>
      <Hell color="red" />
    </Wrpper>
  )
}

export default App;
```
