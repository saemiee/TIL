## SPA

> Single Page Application(싱글 페이지 어플리케이션)은 모던 웹의 페러다임이다. SPA는 단일 페이지로 기존의 서버 사이드 렌더링과 비교할 때, 배포가 간다하며 네이트브 앱과 비슷한 사용자 경험을 제공한다는 장점이 있다.

### SPA의 장점

- 서버에서 페이지들을 그리는 코드 작업을 할 필요가 없다. -> 페이지를 그리는 작업을 모두 프론트단에서 처리함.
- 페이지 리로드가 없다.

### SPA의 단점

- 앱의 규모가 커지면 파일 사이즈가 너무 커진다. -> 유저가 실제로 방문하지 않을수도 있는 페이지에 관련된 렌더링 관련 스크립트도 불러옴.
- 초기 구동속도가 느린 편이다.
- SEO(검색엔진 최적화) 문제가 존재한다. -> SPA는 서버 렌더링 방식이 아닌 JS 기반 기봉기 모델(클라이언트 렌더링 방식)이다. 때문에 처음 받은 웹 페이지의 소스코드가 거의 비어있어 검색이 잘 되지 않을 수 있다.

> #### SEO란? 검색자의 의도를 이해하고 이에 맞춰 웹 페이지의 콘텐츠를 제작, 검색 결과 페이지에서 잘 노출 되도록 웹페이지의 태그와 링크 구조를 개선하여 자연 유입 트래픽을 늘림

---

## MAP란?

> 브라우저에서 변경사항이 있을 때 서버로 서브밋 데이터를 전달해 새로운 페이지 렌더링 요청 시 정적 리소스가 다운로드 되고 전체 페이지를 다시 렌더링하게 된다.(새로고침이 발생해 사용성이 좋지 않다.) SPA보다는 규모가 더 크다.

### MPA의 장점

- 시작적 맵이 필요한 사용자에게 적합하다.
- SPA와 달리 SEO에 친화적이다.
- SPA와 달리 첫 로딩이 짧은 편이다.

### MPA의 단점

- 상태를 유지하기 번거러워진다.
- 불필요한 로딩이 발생한다.
- 개발이 매우 복잡해진다.