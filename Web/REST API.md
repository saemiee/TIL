## REST

> Reperesentational State Transfer, 자원을 이름으로 구분하여 해당 자원을 상태를 주고받는 모든 것을 의미한다.

1. HTTP URI을 통해 자원을 명시하고,
2. HTTP Method(get,post,delete,patch)를 통해
3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미한다.

### CRUD Operation ?

> CRUD는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Creat(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말로 REEST에서의 CRUD Operation 동작 예시는 다음과 같다

```
Create: 데이터 생성(POST)
Read: 데이터 조회(GET)
Update: 데이터 수정(PUT, PATCH)
Delete: 데이터 삭제(DELETE)
```

### REST 구성요소

1. 자원: HTTP URI
2. 자원에 대한 행위: HTTP Method
3. 자원에 대한 행위의 내용: HTTP Message Pay Load

### REST의 특징

1. 서버 클라이언트 구조
2. 무상태
3. 캐시 처리 가능
4. 계층화
5. 인터페이스 일관성

### REST의 장단점

[장점]

- HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없다.
- HTTP 프로토콜의 표준을 최대한 활용해 여러 추가적인 장점을 함꼐 가져갈 수 있게 해준다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
- Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다.
- REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악이 가능하다.
- 여러 가지 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
- 서버와 클라이언트의 역할을 명확하게 분리한다.

[단점]

- 표준이 자체가 존재하지 않아 정의가 필요하다.
- HTTP Method 형태가 제한적이다.
- 브라우저를 통해 테스트할 일이 많은 서비스람녀 쉽게 고칠 수 있는 URL보다 Header 정보의 갑을 처리해야 하므로 전문성이 요구된다.
- 구형 브라우저에서 호환이 되지 않아 지원해주지 못하는 동작이 많다.

## REST API

> REST의 원리를 따르는 API를 의미한다. REST API를 올바르게 설계하기 위해서는 지켜야 하는 몇가지 규칙을 따라야 한다.

### GET

주로 데이터를 읽거나 검색시 사용되는 메소드. 만약 GET 요청이 성공적으로 이루어진다면 XML이나 JSON과 함꼐 200 HTTP 응답 코드를 리턴한다. 에러가 발생하면 주로 404 에러나 400 에러가 발생한다.

- 데이터를 읽을때만 사용되고 수정할 때는 사용하지 않는다.
- 같은 요청을 여러 번 하더라도 변함없이 항상 같은 응답을 받을 수 있다.
- 데이터를 변경하는 연산ㅇ네 사용하면 안된다.

```
GET /user/1
```

### POST

새로운 리소스를 생성할 때 사용된다. 조금 더 구체적으로는 POST는 하위 리소스들을 생성하는데 사용된다. 성공적으로 creation을 완료하면 201 HTTP 응답을 반환한다.

- 같은 POST 요청을 반복해서 했을 때 항상 같은 결과물이 나오는 것을 보장하지 않는다.
- 두 개의 같은 POST 요청을 보내면 같은 정보를 담은 두 개의 다른 resource를 반환할 가능성이 높다.

```
POST /user
body: {date : "example"}
Content-Type : "application/json"
```

### PUT

리소스를 생성/업데이트하기 위해 서버로 데이터를 보내는데 사용된다.
동일한 PUT 요청을 여러 번 호출하면 항상 동일한 결과가 생성된다.

```
PUT /user/1
body : {date : "update example"}
Content-Type : "applicatino/json"
```

### DELETE

지정된 리소스를 삭제한다.

```
DELETE /user/1
```

## RESTful

REST의 원리를 따르는 시스템을 의미한다. 하지만 REST를 사용했다 하여 모두 RESTful 한 것은 아니다. REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTful하다 말할 수 있으며 모든 CRUD 기능을 POST로 처리 하는 API 혹은 URI 규칙을 올바르게 지키지 않은 API는 REST API 설계 규칙을 올바르게 지키지 못한 시스템은 REST API를 사용하였지만 RESTful 하지 못한 시스템이다.
