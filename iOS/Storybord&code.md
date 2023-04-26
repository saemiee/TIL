## Storybord VS Code Base

Code Base로 개발하기 전 Stroybord와 Code Base로 개발의 차이점을 공부해보기 !

### Storybord

- 장점

  - 결과물에 관해 예측이 쉽다.
  - 소스코드 하나하나를 기억하지 않아도 된다.
  - Inspector 창에서 속성을 확인, 설정할 수 있다.

- 단점
  - 파일이 굉장히 무거워진다.
  - IBOutlet, IBAction 등 연결이 끊어졌을 때 알기 힘들다.
  - Storybord를 코드로 봤을 때 코드리뷰가 어렵다.
  - Conflict 무조건 발생한다.

### Code Base

- 장점

  - 비교적 파일이 가벼워진다.
  - 상대적으로 코드를 알아보기 쉽다.
  - Conflict 발생 가능성이 상대적으로 낮아진다.

- 단점
  - 어떤 화면이 만들어질지 예측하기 어렵다.
  - Code가 길어진다.
  - Component의 속성을 어느정도 숙지해야 한다.
