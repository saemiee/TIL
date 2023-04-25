## useRef

저장공간 또는 DOM 요소에 접근하기 위해 사용되는 React Hook이다. 여기서 Ref는 reference 참조를 뜻한다. 일반 자바스크립를 사용할 때는 특정 DOM을 선택하기 위해서 querySelector 등의 함수를 사용한다. React에서도 가끔 DOM 을 직접 선택해야는 상황이 필요할 대 useRef를 사용한다.

### useRef로 DOM 요소 선택하기

```
// InputSample.js
import React, { useState, useRef } from 'react';

const InputSample = () => {
  const [inputs, setInputs] = useState({
    name: '',
    nickname: ''
  });

  const { name, nickname } = inputs;

  const nameInput = useRef();

  const onChange = (e) => {
    const { value, name } = e.target;
    setInputs({
      ...inputs,
      [name]: value
    });
  };

  const onReset = () => {
    setInputs({
      name: '',
      nickname: ''
    });
    nameInputs.current.focus();
  };

  return (
    <div>
      <input
        name="name"
        placeholder="이름"
        onChange={onChange}
        value={name}
        ref={nameInput}
      />
      <input
        name="nickname"
        placeholder="닉네임"
        onChange={onChange}
        value={nickname}
      />
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값: </b>
        {name} ({nickname})
      </div>
    </div>
  );
}

export default InputSample;
```

- `useRef()`를 사용해 Ref 객체를 만든다.
- 만든 객체를 선택하고 싶은 DOM에 `ref` 값으로 설정한다. -> `.current` 값은 원하는 DOM을 가르킨다.
- 예저에서는 onReset 함수에서 input에 포커스를 하는 focus() DOM API를 호출했다.

### useRef로 변수 관리하기

useRef는 DOM을 선택하는 용도 외에도 컴포넌트 안의 조회 및 수정 할 수 있는 변수를 관리하는 용도로 사용된다.
useRef로 관리하는 변수는 값이 바뀐다고 해서 컴포넌트가 리렌더링 되지 않는다. 컴포넌트에서의 상태는 상태를 바꾸는 함수를 호출하고 나서 그 다음 렌더링 이후 업데이트 된 상태를 조회 할 수 있는 반면 useRef로 관리하는 변수는 설정 후 바로 조회가 가능하다.

- settimeout, seInterval 을 통해 만드어지 id
- 외부 라이브러리를 사용해 생성된 인스턴스
- scroll 위치

```
// UserList.md
import React from 'react';

const User = ({user}) => {
  retrun (
    <div>
      <b>{user.name}</b> <span>({user.email})</span>
    </div>
  )
}

const UserList = ({users}) => {
  return (
    <div>
      {users.map(user => (
        <User user={user} key={user.id} />
      ))}
    </div>
  )
}

export default UserList;
```

```
// App.js
import React, { useRef } from 'react';
import UserList from './UserList';

const App = () => {
  const users = [
    {
      id: 1,
      username: 'saemi',
      email: 'public.saemi@gmail.com'
    },
    {
      id: 2,
      username: 'tester',
      email: 'tester@example.com'
    },
    {
      id: 3,
      username: 'cat',
      email: 'cat@example.com'
    }
  ];

  const nextId = useRef(4);
  const onCreate = () => {
    // 배열에 항목 추가하는 로직

    nextId.current += 1;
  };
  retrun <UserList user={users} />
}

export default App;
```

`useRef`를 사용할 때 파라미터를 넣어주면 `.current` 값의 기본값이 된다. 이 값을 수정, 조회하고 싶다면 `.current` 값을 수정, 조회한다.

### useRef를 사용해야 할 때

- 포커스, 텍스트 선택영역, 미디어의 재생을 관리할 때
- 애니메이션을 직접적으로 실행시킬 때
- 서드 파티 DOM 라이브러리를 React와 같이 사용할 때
