## localstorage(임시저장공간) 사용하기

localStrage는 웹 스토리지 객체로 브라우저 내 키-값 쌍으로 저장하도록 도와준다.
localStrage를 사용하면 페이지를 새로 고침하거나 브라우저를 껐다 켜도 데이터가 사라지지 않고 남았을 수 있다.

### 데이터 저장하기

`localStorage.setItem("datalist", data);`
setItem(key, value)

- setItem 메서드를 통해 `key`는 dataList, `value`는 data로 들어간다.
- storage에 저장된 데이터는 모두 문자열만 사용이 가능하다.
- 저장된 데이터 `value`인 data를 문자열로 변환해야한다.
- 값은 반드시 문자열로 저장된다 !!

`localStorage.setItem("datalist", JSON.stringfy(data));`
JSON.stringfy() 를 통해 객체를 문자열로 반환하기

> JSON.stringify: 객체 -> 문자열
> JSON.parse: 문자열 -> 객체

localStorage에 새로 넣어준 값으로 변환하는 것이 아니라 배열처럼 값을 넣어주기 위해서는 배열을 하나 만들어 주고 배열에 하나씩 새로운 값을 넣고 데이터를 담은 배열처럼 setItem() 해야한다.

```
const addData = () => {
  // localStorage에 key: dataList, value: data가 있으면 물러오고 없으면 [] 빈 배열 할당
  const dataArray = JSON.pares(localStorage.getIem("dataList")) || [];
  dataArray.push(data) // 추가할 데이터 객체
  localStorage.setItem("dataList", JSON.stringify(dataArray));
}
```

### 데이터 불러오기

`JSON.parse(localStorage.getItem('dataList'))`
getItem(key) 를 통해 해당 키에 있는 데이터를 불러올 수 있다.

### 데이터 삭제

`removeItem(key)`
해당 키에 있는 데이터를 모두 삭제한다.

#### keyr가 아닌 특정 value만 삭제하고 싶은 때

```
const onDataDelete = (id) => {
  const [data, setData] = useState([]);
  const lefData = data.fileter((item) => item.id ! == id)
  localStorage.setItem('dataList', JSON.stringify(lefData))
  setData(lefData)
}
```

삭제하고 싶은 데이터의 id 값을 받아와 해당 값이 안니 데이터들만 필터링하여 leftData에 담고 그 leftData를 localStorage에 새롭게 setItem()을 해줘야 한다.

### 모든 데이터 삭제

`localStorage.clear();`
localStorage에 있는 모든 key, value를 모두 삭제한다.
