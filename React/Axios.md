## Axios

> Axios는 브라우저, Node.js를 위한 Promise API를 활용하는 HTTP 비동기 통신 라이브러리. 프론트엔드와 백엔드가 통신을 쉽게하기 위해 Ajax와 더불어 사용한다.

### AJAX(Asynchronous Javascript And XML)

자바스크립트의 라이브러중 하나로 브라우저가 가지고 있는 XMLHttpRequest 객체를 활용해 전체 페이지를 새로 고치지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기법이다. 자바스크립트를 사용한 비동기 통신, 클라이언트와 서버간의 XML 데이터를 주고받는 기술이다.
-> 자바스크립를 통해서 서버에 데이터를 요청하는 것

### Axios 특징

- 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 HTTP API 사용
- Promise(ES6) API tkdyd
- 요청과 응답 데이터의 변형
- HTTP 요청 취소 및 요청과 응답을 JSON 형태로 자동 변경

## Axios 사용하기

```
axios
  .get('/user?ID=123')
  // 응답 성공
  .than((res) => {
    console.log(res)
  })
  // 응답 실패
  .catch((err) => {
    console.log(err)
  })
```

### GET

입력한 url 존재하는 자원에 요청을 한다.

```
axios.get(url,[,config])
```

GET은 서버에서 데어터를 가져와서 보여주는 용도이다. 주소에 있는 쿼리스트링을 활용해서 정보를 전달하는 것이지 GET 메서드에서는 값이나 상태등을 바꿀 수 없다.

```
import axios from 'axios';

axios.get('https://localgost:3000/saemi/user').than((Pesponse)=>{console.log(Response.data)})
.catch((Error)=>{console.log(Error)})
```

```
[
  { id: 1, pw: '1234', name: 'saemi' },
  { id: 2, pw: '1234', name: 'cat' },
  { id: 3, pw: '1234', name: 'meow' }
]
```

응답은 json 형태로 넘어온다.

### POST

새로운 리소스를 생성할 때 사용한다.

```
axios.post("usl주소", {
  data객체
    }, [,config])
```

POST 메서드와 두번째 인자는 본문으로 보낼 데이터를 설정한 객체 리터럴을 전달한다.

```
axios.post('url',
  {
    contact: 'saemi',
    email: 'saemi@gmail.com'
  },
  {
    headers: {
      'Content-type': 'application/json',
      'Accept': 'application/json'
    }
  }
)
  .then((response) => {console.log(response.data);})
  .catch((response => {console.log("Error")});
```

### Delete

REST 기반 API 프로그램에서 테이터베이스에 지정되어 있는 내용을 삭제하는 목적으로 사용한다.

```
axios.delete(url,[,config]);
```

Delete 메서드는 HTML Form 태그에서 기본적으로 지원하는 HTTP 메서드가 아니다.
Delete 메서드는 서버에 있는 데이터베이스의 내용을 삭제하는 것을 주 목적으로 하기에 두 번째 인자를 아예 전달하지 않는다.

```
axios.delete("/thisisExample/list/30").then(function(response){
  console.log(response)
  }).catch(function(ex){
    throw new Error(ex)
}
```

### PUT

REST 기반 API 프로그램에서 데이터베이스 저장되어 있는 내용을 갱신하는 목적으로 사용한다.

```
axios.put(url[, data[, config]])
```

PUT 메서드는 HTML From 태그에서 기본적으로 지원하는 HTTP 메서드가 아니다.
PUT 메서드는 서버에 있는 데이터베이스의 내용을 변경하는 것을 주 목적으로 하고있다.

### Axios vs Fetch API

자바스크립트에서 API를 연동하기 위해서 Fetch API를 사용하곤 한다. 리액트도 자바스크립트 built-in 라이브러리중 하나인 Fetch API 라는 API 연동 모듈을 사용한다.
하지만 Fetch API 는 자바스크립의 built-in 라이브러리라는 특성 때문인지 많은 사람들이 리액트에서 axios를 사용하는 것을 선호한다.

```
// Fetch
const url = 'http://localhost3000/test'
const option = {
  method: 'POST',
  header: {
    'Accept':'application/json',
    'Contnet-Type':'application/json';charset=UTP-8'
  },
  body:JSON.stringify({
  	name:'sewon',
    	age:20
  })

  fetch(url,options)
  	.then(response => console.log(response))
```

```
// Axios
const option ={
  url ='http://localhost3000/test`
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  data:{
  	name:'sewon',
    	age:20
  }

  axios(options)
  	.then(response => console.log(response))
```

- Fetch()는 body 프로퍼티를 사용하고, axios는 data 프로퍼티를 사용한다.
- Fetch의 url이 Fetch()함수의 인자로 들어가고 axios 에서는 url이 option 객체로 들어간다.
- Fetch에서 body 부분은 stringify()로 되어진다.

> 이처럼 axios는 HTTP 통신의 요구사항을 컴팩한 패키지로써 사용하기 쉽게 설계 되었다.
