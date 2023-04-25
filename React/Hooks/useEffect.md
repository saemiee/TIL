## useEffect

useEffect 함수는 리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 실행할 수 있도록 하는 Hook

- 페이지가 처음 렌더링 되고 난 후 useEffect는 무조건 한 번 실행된다.
- useEffect에 배열로 지정한 useState의 값이 변경되면 실행된다.

즉, useEffect는 렌더링, 혹은 변수의 값 혹은 오브젝트가 달라지게 되면, 그것을 인지하고 업데이트를 해주는 함수다. useEffect는 콜백 함수를 부르게 되며, 렌더링 혹은 값, 오브젝트의 변경에 따라 어떠한 함수 혹은 여러 개의 함수들을 동작시킬 수 있다.

### useEffect를 사용하는 방법

```
useEffect(() => {});

useEffect(() => {}, []);

const [name, setName] = useState();
useEffect(() => {}, [name]);
```

1. 가장 기본 형태이지만 거의 사용하지 않는다. Dependency가 없기 때문에 렌더링 할 때 한 번 그리고 어떤 작은 요소라도 변화한다면 계속 useEffect가 발동되어 불필요한 실행이 많아진다.

2. useEffect를 렌더링 후 단 한 번만 실행하고 싶을 때 사용한다.
   몰백 함수 뒤에 [] 있는 것은 Dependency를 지정한다. 하지만 아무 변수나 값 없이 대괄호만 있다면 이 useEffect는 렌더링 후 단 한 번만 실행되고 다시는 실행되지 않는다.

3. useEffect를 렌더링 후 한 번, 그리고 배열 안 변수의 값이 변할 때마다 실행하는 코드이다.
   이렇게 Dependency를 지정해서 지정된 변수의 값이 변했을 때만 실행된다.

### useEffect 사용해보기

```
import React, { useEffect, useState } from 'react';

const Number = () => {
  const [number, setNumber] = useState(0);
  const [name, setName] = useState('saemi');

  useEffect(() => {
    console.log('hello');
  }, [name]);

  const counter = () => setNumber(number + 1);
  const nameChangeer = () => setName('cat');

  retrun (
    <div>
      <button onClick={counter}>click</button>
      <button onClick={nameChanger}>change Name</button>
      <div>{number}</div>
      <div>{name}</div>
    </div>
  )
}

export default Number;
```

useEffect에 [] 를 사용하면 렌더링 후 무조건 단 한 번만 실행된 후 더 이상 실행되지 않는다.

### useEffect 정리하기 !

- 어떤 값의 변화가 감지되면, 실행되어 특정 함수나 작업을 실행하는 함수
- useEffect는 콜백함수를 가지며, dependecy는 있을 수도 없을 수도 있다.
- useEffect는 무조건 렌더링 후 한 번 실행된다.
