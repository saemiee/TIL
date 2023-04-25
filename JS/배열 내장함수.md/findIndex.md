## findIndex

만약 배열 안에 있는 값이 숫자, 문자열, 또는 불리언이라면 찾고자하는 항복이 몇번째 원소인지 알아내기 위해서는 indexOf를 사용한다. 하지만 배열 안에 값이 객체나 배열이라면 findIndex를 사용한다.

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

const index = loves.findIndex(love => love.id === 3);
consoloe.log(index);
```
