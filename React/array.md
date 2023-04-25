## 리엑트에서 배열 렌더링하기

동적인 배열을 렌더링해야 할 때는 자바스크립트의 배열 내장함수 `map()` 을 사용한다.
`map()` 함수는 배열 안의 각 원소를 변환해 새로운 배열을 만들어주는 함수이다.

```
// UserList.js
import React from 'react';

cosnt user = ({user}) => {
  return (
    <div>
      <b>{user.username}</b> <span>({user.email}</span>
    </div>
  );
}

const UserList = () => {
  const users = [
    {
      id: 1,
      username: 'saemi',
      email: 'public.saemi@gmail.com'
    },
    {
      id: 2,
      username: 'cat',
      email: 'public.cat#gmail.com'
    },
    {
      id: 3,
      name: 'test',
      email.test@example.com
    }
  ];

  retrun (
    <div>
      {users.map(user => {
        <User user={user key={user.id}}>
      })}
    </div>
  )
}
```

리액트에서 배열을 렌더링 할 때는 `key`라는 props를 설정해야 한다. `key` 값은 각 원소들마다 가지고 있는 고유의 값으로 설정해야 한다. 만약 배열 안의 원소가 갸지고 있는 고유한 값이 없다면 `map()` 함수를 사용 할 때 설정하는 콜백함수의 두번째 파라미터 `index`를 key로 사용한다.

```
<div>
  {users.map((user, index) => (
    <User user={user} key={index} />
  ))}
</div>
```

### key

```
const array = ['s', 'a', 'e', 'm', 'i'];
array.map(item => <div>{item}</div>)
```

key가 존재하지 않는다면 위 코드의 배열을 map 함수를 사용해 렌더링 할 때 a 와 e 사이에 z를 삽입하게 된다면 두 div 사이에 새로운 div가 삽입되는 것이 아니라 기존의 값이 변경이 되고 마지막에 i 가 새로 삽입하는 방식이 된다.
-> 즉, 키가 없다면 비효율적이다.

```
[
  {
    id: 0,
    text: 's'
  },
  {
    id: 1,
    text: 'a'
  },
  {
    id: 2,
    text: 'e'
  },
  {
    id: 3,
    text: 'm'
  }
];
```

key로 사용 가능한 고유 값 존재 -> id

```
array.map(item => <div key={item.id}>{item.text}</div>)
```

key가 존재한다면 배열이 업데이트 될 때 수정되지 않는 기존 값은 그대로 두고 원하는 곳에 내용을 삽입하거나 삭제해 효율적으로 렌더링이 가능하다 !

### 정리

배열을 렌더링 할 때 고유한 key 값은 중요하다!
만약 배열 안에 중복되는 key가 있을 경우 렌더링 시 오류가 콘솔에 나타나며 업데이트가 제대로 이루어지지 않는다.
