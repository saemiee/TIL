## Document.querySelector()

제공한 선택자 또는 선택자 뭉치와 일치하는 문서 내 첫 번째 Element를 반환한다. 일치하는 요소가 없을 경우 null을 반환한다.

```
document.querySelector(selectors);

```

### 반환값

제공한 CSS 선택자를 만족하는 첫 번째 Element 객체. 결과가 없다면 null
선택자를 만족하는 모든 요소의 목록이 필요하다면 `querySelectorAll()`을 사용한다.
