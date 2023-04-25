# Flexbox

flexbox는 행과 열 형태로 항목 무리를 배치하는 일차원 레이아웃 메서드이다. 항목은 부족한 공간에 맞추기 위해 축소되거나 여분의 공간을 채우기 위해 변형된다.

```
<div class="container">
	<div class="item">helloflex</div>
	<div class="item">abc</div>
	<div class="item">helloflex</div>
</div>
```

flexbox의 속성들은 컨테이너에 적용되는 속성, 아이템에 적용되는 속성으로 두가지로 나뉜다.

## Flexbox container에 적용되는 속성

### `display: flex;`

가장 먼저 어떤 요소들을 flexbox로 레이아웃할 요소를 선택한다.
아이템들이 배치된 방향 축을 `main axis` 메인축, 메인축과 수직인 축을 `cross axis` 수직축 또는 교차축이라고 한다.

### `flex-direction` 배치방향 설정

아이템들이 배치되는 축의 방향을 결정하는 속성이다.

- row(기본값) : 아이템들이 행(가로) 방향으로 배치된다.
- row-reverse : 아이템들이 역순으로 가로 배치된다.
- column : 아이템들이 열(세로) 방향으로 배치된다.
- column-reverse : 아이템들이 역순으로 세로 배치된다.

### `flex-wrap` 줄넘김 처리 설정

컨테이너가 더 이상 아이템들을 한 줄에 담을 여유 공간이 없을 때 아이템 줄바꿈을 어떤 방식으로 할지를 결정하는 속성이다.

- nowrap(기본값) : 줄바꿈을 하지 않는다.(만약 넘친다면 삐져나가는 현상이 발생)
- wrap : 줄바꿈을 한다. float 이나 inline-block으로 배치한 요소들과 비슷하게 동작한다.
- wrap-reveres : 아이템들을 역순으로 배치해 줄바꿈을 한다.

### `flew-flow`

`flex-direction`과 `flex-wrap`을 한 번에 지정할 수 있는 단축 속성이다. `flex-direction`, `flex-wrap`의 순으로 한 칸 떼고 작성한다.

`justify`는 메인축 방향으로 정렬, `align`은 수직축 방향으로 정렬을 의미한다.

### `justif-content` 메인축 방향 정렬

- flex-start(기본값) : 아이템들을 시작점으로 정렬한다. flex-direction이 row일 때는 왼쪽, column일 때는 위쪽에 정렬한다.
- flex-end : 아이템들을 끝점으로 정렬한다. flex-direction이 row일 때는 오른쪽, column일 때는 아래쪽에 정렬한다.
- center : 아이템들을 가운데로 정렬한다.
- space-between : 아이템들의 사이에 균일한 간격을 만들어준다.
- space-around : 아이템들의 둘레에 균일한 간격을 만들어준다.
- space-evenly : 아이템들의 사이와 양 끝에 균일한 간격을 만들어준다.(IE와 엣지에서는 지원되지 않음

### `align-item` 수직축 방향 정렬

- streth(기본값) : 아이템들이 수직방향으로 끝까지 쭉 늘어난다.
- flex-start : 아이템들을 시작점으로 정렬한다. flex-direction이 row(가로 배치)일 때는 위, column(세로 배치)일 때는 왼쪽에 배치한다.
- flex-end : 아이템들을 끝점으로 정렬한다. flex-direction이 row일 때는 아래, column일 때는 오른쪽에 배치한다.
- center : 아이템들을 가운데로 정렬한다.
- baseline : 아이템들을 텍스트 베이스라인 기준으로 정렬한다.

`justify-content: center;` `align-item: center;` 를 사용하면 아이템을 한 가운데 놓을 수 있다.

### `align-content` 여러행 정렬

flex-wrap: wrap;이 설정된 상태에서 아이템들의 행이 2행 이상이 되었을 때 수직축 방향 정렬을 결정하는 속성이다.

## Flexbox item에 적용되는 속성

### `flex-basis` 유연한 박스의 기본 영역

flex-basis는 flex item의 기본 크기를 설정한다.

- flex-basis의 값으로는 width, heigh 등에 사용하는 각종 단위의 수가 들어갈 수 있다.
- 기본값 auto는 아이템의 width 값을 사용하며 width 값을 설정하지 않으면 컨텐츠의 크기가 된다.

### `flex-grow` 유연하게 늘리기

flex-grow는 아이템이 flex-basis의 값보다 커질 수 있는지를 결정하는 속성이다.
기본값이 0이기 때문에 따로 적용하기 전까지는 아이템이 늘어지 않는다.

### `flex-shrink` 유연하게 줄이기

flex-basis의 값보다 작아질 수 있는지를 결정하는 속성이다.
기본값이 1이기 때문에 따로 적용하기 전에도 아이템이 줄어들 수 있다.

### `flex`

flex-grow, flex-shrink, flex-basis를 한 번에 쓸 수 있는 축약형 속성이다.

### `align-self` 수직축으로 아이템 정렬

align-items가 전체 아이템의 수직축 방향 정렬이라면, align-self는 해당 아이템의 수직축 정렬이다.

### `order` 배치 순서

각 아이템들의 시각적 순서를 나열하는 속성이다.

### `z-index`

z-index로 z축 정렬을 할 수 있다. 숫자가 클 수록 위로 올라온다.
