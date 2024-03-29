## CocoaPods VS SPM

> iOS 앱 개발시 라이브러리를 추가하여 사용하는 방법은 CocoaPods, SPM, Carthage 이렇게 3가지가 있다. 오늘은 CoCoaPods와 SPM의 장단점을 알아보자 !

### CocoaPods

- 장점

  - 사용하기 쉽다.
  - Dynamic, Static 라이브러리를 모두 지원한다.
  - 의존성의 의존성까지 자동으로 관리한다.
  - pod outdated 명령어로 쉽게 새로운 버전이 있는지 체크할 수 있다.
  - 대부분의 라이브러리는 코코아팟을 지원한다.

- 단점
  - 라이브러리를 다운받아 설치 하는데 오랜 시간이 걸린다.
  - 프로젝트를 빌드 할 때마다 모든 팟 라이브러리가 같이 빌드되므로 다른 도구를 사용할 때 보다 빌드 시간이 느리다.

### SPM(Swift Package Manager)

- 장점

  - 애플이 지원한다.
  - 의존성의 의존성까지 자동으로 관리한다.
  - 누구나 쉽게 어떤 의존성이 애플리케이션에 있는지 알 수 있다.
  - Swift 언어에 built-in 되어잇어 별다른 설치가 필요없다.
  - Package.swift 파일 이외에 수행할 설정이 없다.
  - Xcode이 GUI 환경에서 관리가 가능하다.

- 단점
  - 아직 지원하지 않는 라이브러리가 많다.
  - 아직 해결되지 않은 버그 이슈가 많다.
