# 230907-1 / SWIFT / closure의 경량화 문법 (2)

```swift
func klosure(closure: (Int, Int, Int) -> Int) {
    closure(1, 2, 3)
}
```

위와 같은 함수를 호출할 때에는 

```swift
klosure(closure: { (a: Int, b: Int, c: Int) -> Int in
    return a + b + c
})
```

이렇게 작성해야하는데, 이를 경량화 문법으로 매우 짧고 간단하게 줄일 수 있다.

### 파라미터 형식과 리턴 형식을 생략

위 코드에서 파라미터 형식과 리턴 형식은 

```swift
klosure(closure: { (a: Int, b: Int, c: Int) -> Int in 
    return a + b + c
})
```

> a, b, c의 타입을 가리키는 Int, 리턴 형식인 Int 이다. 

즉 

```swift
klosure(closure: { (a, b, c) ->  in 
    return a + b + c
})
```

이렇게 생략해서 쓸 수 있는 것이다. 

### Parameter Name은 Shortand Argument Names으로 대체하고, Parameter Name과 in 키워드를 삭제

`Shortand Argument Names` 는 조금 생소하다.

간단하게 설명하자면

```swift
klosure(closure: { (a, b, c) ->  in 
    return a + b + c
})
```

a, b, c 라는 파라미터 이름 대신 

```swift
a → $0
b → $1
c → $2
```

이렇게 $와 index를 이용해 순서대로 파라미터에 접근하는 것이다. 

따라서 경량화된 문법은

```swift
klosure(closure: {   
    return $0 + $1 + $2
})
```

이렇게 간단화 할 수 있다. 

### 단일 리턴문만 남을 경우, return도 생략

```swift
klosure(closure: {   
    return $0 + $1 + $2
})
```

단일 리턴문은 클로저 내부에 리턴 구문이 하나만 있는 경우를 말한다. 

위 코드의 경우 리턴문이 하나이기에, 생략할 수 있다.

```swift
klosure(closure: {   
    $0 + $1 + $2
})
```

아직 끝이 아니다. 

### 클로저 파라미터가 마지막 파라미터면, 트레일링 클로저로 작성한다

<a href = "https://github.com/kimkyumbi/TIL/blob/main/iOS/230904-1.md" > Trailing Closure </a>

위 글에서 Trailing Closure를 알아보았다. 

그렇다면 더 간결하게 생략할 수 있다. 

```swift
klosure() {  
     $0 + $1 + $2
}
```

이렇게 말이다. 

그리고 `()` 까지 생략해서,

```swift
klosure {  
     $0 + $1 + $2
}
```

최종적으로 이런 코드로 바뀌게 된다. 

### Before

```swift
klosure(closure: { (a: Int, b: Int, c: Int) -> Int in
    return a + b + c
})
```

### After 

```swift
klosure {  
     $0 + $1 + $2
}
```