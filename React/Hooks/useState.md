## useState

기본적인 Hooks로 함수형 컴포넌트에서도 가변적인 상태를 지니게 해준다.

```
import useSate from 'react';

const [saemi, setSaemi] = useSate(0);
```

useState를 사용할 때는 상태의 기본값을 파라미터로 넣어 호출한다. 이 함수를 호출하면 배열이 반환되는데 첫번째는 원소는 현재 상태, 두번째 원소는 Setter 함수이다.

### 동적인 값 끼얹기

컴포넌트에서 동적인 값을 상태(state)라고 부른다. useState를 사용하면 컴포넌트에서 상태 관리가 가능하다.

```
// Counter.js
import React. { useState } from 'react';

const Counter= () => {
  const [number, setNumber] = useState(0);

  const onIncrease = () => {
    setNumber(number + 1);
  }

  const onDecrease = () => {
    setNumber(number -1);
  }

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  )
}

export default Counter;
```

### 함수형 업데이트

setState는 불필요한 렌더링을 방지하면서 성능을 향상시키기 위해 즉시 함수를 수해아지 않도록 설계되었다. 이러한 작동방식을ㄴ 비동기적으로 작동한다고 이야기 할 수 있다.

```
import { useState } from 'react';

export defautl const New = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount((prev) => prev + 1)
    setCount((prev) => prev + 1)
    setCount((prev) => prev + 1)
    setCount((prev) => prev + 1)
    setCount((prev) => prev + 1)
  }
}
```

1. `const [ count, setCount ] = useState(0)`에서 선언된 `count` 값 0을 `prev`라는 임시저장 공간에 담는다.
2. 임시저장공간에 담긴 `prev에` + 1을 한 후 다시 임시저장공간 `prev`에 담는다.
3. `prev`에 + 1 한 수 다시 `prev`에 담는다.
4. 같은 방식으로 진행 후 최종적으로 `setCount((prev) => prev + 1)`에서 4가 담긴 prev에 + 1을 하여 setCount(5)를 실행한다.
