## filter

배열에서 특정 조건을 만족하는 값들만 따로 추출해 새로운 배열을 만든다.

```
const loves = [
  {
    id: 1,
    love: '고양이',
    truee: true
  },
  {
    id: 2,
    love: '체리',
    truee: true
  },
  {
    id: 3,
    love: '복숭아',
    truee: true
  },
  {
    id: 1,
    love: '아침',
    truee: false
  }
];

const hate = loves.filter(love => love.truee === false);
console.log(hate);

<!-- [
  {
    id: 1,
    love: '아침',
    truee: false
  }
] -->

```
