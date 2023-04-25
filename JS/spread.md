## spread

spread는 ES6 에서 도입된 문법이다.

### spread

spread는 펼치다, 퍼뜨리다라는 의미이다. 이 문법을 사용하면 객체 혹은 배열을 펼칠 수 있다.

```
const cat = {
  name: '소금'
};

const cuteCat = {
  ...cat,
  attribute: 'cute'
};

const blackCuteCat = {
  ...cuteCat,
  color; 'black'
};

console.log(cat);
console.log(cuteCat);
console.log(blackCuteCat);
```

```
const animals = ['고양이', '호랑이', '사자'];
const anotherAnimals = [...animals, '강아지'];
console.log(animals);
console.log(anotherAnimals);
```
