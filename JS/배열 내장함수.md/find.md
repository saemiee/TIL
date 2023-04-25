## find

find 함수는 findIndex 와 비슷한데, 찾아낸 값이 몇 번째 원소인지 알아내는 것이 아니라 찾아낸 값 자체를 반환한다.

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

const love = loves.find(love => love.id === 3);
consoloe.log(love);

// {id: 3, love: "복숭아", truee: true}
```
