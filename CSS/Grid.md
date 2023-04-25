# Grid

Grid와 Flex의 큰 차이점은 Flex는 한 방향 레이아웃 시스템(1차원)이지만 Grid는 두 방향 레이아웃 시스템(2차원)으로 더 복합적인 레이아웃 표현이 가능하다.

## Grid container에 사용되는 속성

### display: grid;

grid 컨테이너에 display: grid;를 적용하는 것이 grid의 시작이다. 만약 아이템들이 block 요소라면 이 한 줄 만으로 변화가 일어나지 않는다.

### gird-template-rows(columns)

컨테이너에 그리드 트랙의 크기들을 지정해주는 속성이다.

```
grid-template-columns: 200px 200px 500px;
grid-template-rows: 1fr 1fr 1fr;
```

### repeat 함수

repeat는 반복되는 값을 자동으로 처리할 수 있는 함수이다. repeat(반복횟수, 반복값)

### minmax 함수

최솟값과 최댓값을 지정할 수 있는 함수이다.

### row(column)-gap

그리드 셀 사이의 간격을 설정하는 속성이다.
