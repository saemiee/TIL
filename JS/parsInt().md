## parsInt()

`parsInt()` 함수는 문자열 인자를 파싱하여 특정 진수의 정수를 반환하는 함수이다.

```
parseInt(string)
parseInt(string, radix)
```

### 매개변수

- `string` - 숫자로 변환할 문자열
- `radix` - string의 진수는 2부터 36까지의 정수이다.

### NaN을 반환하는 경우

- 공백이 아닌 첫 문자를 숫자로 변환할 수 없는 경우
- `radix`가 2보다 작거나 36보다 큰 경우
