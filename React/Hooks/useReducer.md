## useReducer

useReducer는 State(상태)를 관리하고 업데이트 하는 Hook인 useState를 대체할 수 있는 Hook 이다. 즉, useReducer는 useState처럼 State를 관리하고 업데이트 할 수 있는 Hook이다.

useReducer는 한 컴포넌트 내에서 State를 업데이트하는 로직 부분을 그 컴포넌트로부터 분리시키는 것을 가능하게 해준다. useReducer는 State 업데이트 로직을 분리해 컴포넌트 외부에 작성하는 것을 가능하게 함으로써, 코드의 최적화를 이루게 해준다.

### useReducer vs useState

useReducer, useState 모두 State를 변경하고 관리할 때 사용한다. 그럼 각 언제 사용해야 좋을까 ?

- useState

  - 관리해야 할 State가 1개일 경우
  - 그 State가 단순한 숫자, 문자열 또는 Boolean 값일 경우

- useReducer
  - 관리해야 할 State가 여러 개인경우, 복수일 경우
  - 현재는 단일 State 값만 관리하지만 추후 유동적일 경우
  - 스케일이 큰 프로젝트
  - State의 구조가 복잡해질 것으로 보이는 경우

### useReducer의 사용법과 구조

useReducer를 사용하기 위한 구성 요소로 크게 4가지가 있다.

- useReducer 함수
- action
- dispath 함수
- reducer 함수

```
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch(action.type) {
    case "decrement":
      return { count: state.count -1 };
    case "increment":
      return { count: state.count + 1 };
    default:
      throw new Error("Unsupported action type:", action.type);
  }
}

function Counter() {
  const [number, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      {/* 현재 카운트 값은 state인 number 객체의 count로부터 읽어옴 */}
      <h1>Count: {number.count}</h1>
      {/* 카운트 값의 변경을 위해 각 버튼이 클릭되면 dispatch 함수가 발동되면서 reducer 함수가 실행됨.
          dispatch 함수의 인자로, action 객체가 설정되었는데,
          action 객체의 type에는 어떤 버튼을 클릭하였는지에 따라
          "decrement" 또는 "increment"가 들어감
      */}
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
    </>
  )
}

export default Counter;
```

##### useReducer 함수

useReducer 함수는 첫번째 인자인 reducer 함수가 반환하는 값으로 state를 갱신하는 역할을 한다.

```
const [state, dispatch] = useReducer(reducer, initialState, init);
```
