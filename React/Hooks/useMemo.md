## useMemo

리액트에서 컴포넌트의 성능을 최적화 하는데 사용하는 훅이다.

useMemo는 동일한 값을 반환하는 함수를 반복적으로 호출해야 한다면 처음 값을 계산할 대 해당 값을 메모리에 저장해 필요할 때마다 다시 계산하지 않고 메모리에 저장해 필요할 때마다 다시 계산하지 않고 메모리에서 꺼내서 재사용하는 것이다.

### useMemo 구조

```
const value = useMemo(() => {
  return calculate();
}, [item])
```

useMemo는 useEffect처럼 첫번째 인자로 콜백함수, 두번째 인자로 의존성 배열을 받는다.

의존성 배열 안에 있는 값이 업데이트 될 때만 콜백 함수를 다시 호출하여 메모리에 저장된 값을 업데이트 해준다.

만약 빈 배열을 넣는다면 useEffect와 마찬가지로 마운트 될 때만 값을 계산하고 그 이후로 계속 memoization된 값을 꺼내와 사용한다.

### useMemo 사용해보기

```
import React, { useMemo } from 'react';

const Memo = ({ v1, v2 }) => {
  const value = useMemo(() => {
    retrun v1 + v2;
  }, [v1]);

  return <div>{value}</div>;
};

export default Memo;
```

첫번째 매개변수로 콜백함수를 입력하고, 두번째 매개변수로 배열을 입력한다.

첫번째 매개변수 return 값을 기억하고 있고 그 값을 value에 할당한다. 두번째 매개변수 배열의 값이 변경되지 않았다면 이전에 반환했던 값을 재사용한다. 만약 바뀌었다면 useMemo 첫번째 매개변수인 함수를 재실행하여 그 return 값을 기억한다.

정리하면 v1 값이 변경된다면 한 번 함수가 실행되고, 바뀌지 않는다면 이전 retrun 값을 재사용한다.
