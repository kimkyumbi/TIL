# 231001-1 / SWIFT / 제네릭(Generic)

## 정의 

제네릭이란 타입에 의존하지 않는 범용 코드를 작성할 때 사용한다

제네릭을 사용하면 중복을 피하고, 코드를 유연하게 작성할 수 있다

Generic은 가장 강력한 기능 중 하나다

### 제네릭 함수

우리가 만약 인자로 오는 두 Int 타입의 값을 swap하는 함수를 만들고 싶다면,

```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
   let temp = a
   a = b
   b = temp
}
```

위 같은 경우엔 파라미터 모두 Int형일 경우엔 문제 없이 돌아간다.

근데 이 만약 파라미터 타입이 Double, String일 경우엔 사용할 수 없다.

이럴 때 사용하는 것이 바로 제네릭이다.

타입에 제한을 두지 않는 코드를 사용하고 싶을 때 쓴다.

```swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
   let temp = a
   a = b
   b = temp
}
```

`<>`를 이용해서 안에 타입처럼 사용할 이름(T)를 선언해주면,

그 뒤로 해당 이름(T)를 타입처럼 사용할 수 있다.

여기서 이 T를 Type Parameter라고 부르는데, 

T라는 새로운 형식이 생성되는 것이 아니라 

실제 함수가 호출될 때 해당 매개변수의 타입으로 대체된다.

따라서 이렇게 swapTwoValues라는 함수를 제네릭으로 선언해 주면,

```swift
var someInt = 1
var aotherInt = 2
swapTwoValues(&someInt,  &aotherInt) // 함수 호출 시 T는 Int 타입으로 결정
 
 
var someString = "Hi"
var aotherString = "Bye"
swapTwoValues(&someString, &aotherString) // 함수 호출 시 T는 String 타입으로 결정된
```

이렇게 함수를 호출할 때 타입이 지정되게 되는 것이다.