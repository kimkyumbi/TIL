# 230906-1 / SWIFT / closure의 경량화 문법 (Trailing closure)

## 정의 

함수의 마지막 파라미터가 클로저일 때, 이를 파라미터 값 형식이 아닌 함수 뒤에 붙여 작성하는 문법

이때, Argument Label은 생략한다.

일단 예제부터 보면 이해되니 예제를 보자.

### 파라미터가 클로저 하나인 함수

```swift
func klosure(closure: () -> ()) {
    closure()
}
```

클로저 하나만을 파라미터로 받는 함수가 있을 때, 함수를 호출하려면 

```swift
klosure(closure: { () -> () in
    print("Hello!")
})
```

이렇게 써야 했다.

하지만 형식이 간단하지 않기 때문에 헷갈리기 쉽다.

그래서 이 클로저를 파라미터 값 형식으로 보내는 것이 아닌,

함수의 가장 마지막에 클로저를 꼬리처럼 덧붙여서 쓸 수 있다.

```swift
klosure () { () -> () in
    print("Hello!")
}
```

더 진화해서 파라미터가 클로저 하나일 경우엔 호출구문인 `()` 도 생략해줄 수 있다.

결과적으로,

```swift
// 생략 전
klosure(closure: { () -> () in
    print("Hello!")
})

// 생략 후
klosure { () -> () in
    print("Hello!")
}
```

생략 전보다 생략 후가 훨씬 더 간단하게 변했다. 