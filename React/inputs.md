## useState를 사용해 여러 개이 input 상태 관리해보기

### input 관리하기

```
// InputSample.js
import React, { useState } from 'react';

cosnt InputSample = () => {
  const [text, setText] = useState('');

  const onChage = (e) => {
    setText(e.target.value);
  };


  const onReset = () => {
    setText('');
  };
  rn (
    <div>
      <input onChange={onChnage} value={text}/>
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값: </b>
      </div>
    </div>
  )
}

export default InputSample;
```

```
// App.js
import React from 'react';
import InputSample from './InputSample';

const App = () => {
  retrun (
    <InputSample />
  )
}

export default App;
```

- 객체의 `e.target`은 이벤트가 발생한 DOM인 input DOM을 가르킨다.
- 이 DOM의 `value` 값, 즉 `e.target.value`를 조회하면 현재 input에 입력한 값이 무엇인지 알 수 있다.

### 여러 개의 input 관리히기

input의 개수가 여러개가 됐을 때는 단순히 useState를 여러 번 사용하고 onChange도 여러개 만들어서 구현 할 수도 있다. 하지만 좋은 방법은 input에 name을 설정하고 이벤트가 발생했을 때 이 값을 참조하는 방법이다. useState에서는 문자열이 아니라 객체 형태의 상태를 관리해주어야 한다.

```
// InputSample.js
import React, { useState } from 'react';

const InputSample = () => {
  const [inputs, setInputs] = useState({
    name: '',
    nickname: '';
  });

  const { name, nickname } = inputs;

  const onChage = (e) => {
    const { value, name} = e.target;
    setInputs({
      ...inputs,
      [name]: value
    })
  };

  const onReset = () => {
    setInputs({
      name: '',
      nickname: '',
    })
  }

  return (
    <div>
      <input name="name" onChange={onChange} value={name} />
      <input name="nickname" onChange={onChange} value={nickname}/>
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값: </b>
        {name} ({nickname})
      </div>
    </div>
  )
}

export default InputSample;
```

리액트에서 객체를 수정할 때는 새로운 객체를 만들어서 새로운 객체에 변화를 주고 이를 상태로 사용해야 한다.

```
setInputs({
  ...inputs,
  [name]: value
});
```

불변성을 지켜주어야만 리액트 컴포넌트에서 상태가 업데이트 됐음을 감지 할 수 있고, 필요한 리렌더링이 진행된다.
