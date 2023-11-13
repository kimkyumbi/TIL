# 230830-1 / SWIFT / 함수(func)

## 함수란? 

Swift의 함수는  총 3가지의 필수 요소를 포함합니다. 

__함수 이름__, __매개 변수__ (Prameter), __반환타입__ (Return Type)

__재정의__ ( 오버라이드: Override ), __중복 정의__ ( 오버로드: Overload )를 모두 지원합니다. 

### 함수의 정의 

```swift
// swift 함수의 기본적인 형태
func 함수이름(매개변수...) -> 반환 타입 {
	실행 구문
    return 반환 값
}
```

`func`를 써서 만들며 `->`로 반환 타입을 알려준다. 

### Example 

```swift
func hello(friend: String, name: String, age: Int) { // 함수 정의
    print("hello \(friend)! I'm \(name), and \(age) years old") // 실행 구문
}
```