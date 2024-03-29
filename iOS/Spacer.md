# 230726-1 / SWIFT / Spacer

## 정의
```
포함하는 스택 레이아웃의 주요 축을 따라 확장되거나 스택에 포함되지 않은 경우,
두 축 모두에서 확장되는 유연한 공간
```

### Spacer는 기본적으로 사용 가능한 전체 공간을 띄운다.

우리는 타자칠 때 글자 사이를 띄우고 싶을 때 스페이스 바를 친다.

마찬가지로, View 간의 간격을 "띄우고 싶을 때" 사용하는 것이 바로 Spacer이다.

## 예제

```swift
HStack(spacing: 0) {
    Text("엄")      
        .background(.red)
        .font(.system(size: 40))
    Text("준")
        .background(.yellow)
        .font(.system(size: 40))
    Text("식")
        .background(.blue)
        .font(.system(size: 40))
}
```

이 코드는 

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018543107559444/2023-07-26_9.43.14.png?ex=651e5ba2&is=651d0a22&hm=377882399c7f471a4cd7966ec842aab57e68372257e121e9d8e674231f33d9aa&)

이런 Text를 출력해주는데 

만약 각 글자 사이의 간격을 띄우고 싶다면?

이때 Spacer를 사용한다.

```swift
HStack(spacing: 0) {

    Spacer() // Spacer 사용

    Text("엄")      
        .background(.red)
        .font(.system(size: 40))
    Text("준")
        .background(.yellow)
        .font(.system(size: 40))
    Text("식")
        .background(.blue)
        .font(.system(size: 40))
}
```

이렇게 Text위에 Spacer를 사용하면 

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018543367602176/2023-07-26_9.48.27.png?ex=651e5ba2&is=651d0a22&hm=758bd730a7f2c27b84110cb6b56c4d9c9c6ce16625dc133fdfecfbc95ed77be6&)

오른쪽으로 이동하게 된다.

글자 사이의 간격을 띄우고 싶다면 Text사이에 Spacer를 써주면 된다.

### 만약 Spacer를 중복해서 사용한다면?

```swift
HStack(spacing: 0) {

    Spacer() // Spacer 사용

    Text("엄")      
        .background(.red)
        .font(.system(size: 40))

    Spacer() // Spacer 중복 사용

    Text("준")
        .background(.yellow)
        .font(.system(size: 40))

    Spacer() // Spacer 중복 사용

    Text("식")
        .background(.blue)
        .font(.system(size: 40))

    Spacer() // Spacer 중복 사용

}
```

Spacer를 중복해서 사용한다면, 사용 가능한 전체 공간을 Spacer의 수만큼 등분한다. 

위의 코드는 Spacer를 4번 사용했기 때문에, 사용 가능한 전체 공간을 4등분하는 것이다.

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018543602475069/2023-07-26_9.59.27_.png?ex=651e5ba2&is=651d0a22&hm=e15a32504fe23f6d52b37d0abba4a4dee10b56df9839f352fff122214a7e5e0e&)

즉, Spacer를 n개 선언하면, 사용가능한 겅간을 n등분 하는 것이다.

## 여백의 크기 지정 

### minLength 파라미터 

Spacer를 생성할 때 위에서 썼던 것처럼 파라미터를 전달하지 않아도 되지만,

파라미터로 minLength라는 값을 지정할 수 있다.

```swift
HStack(spacing: 0) {

    Spacer(minLength: 100) // minLength의 값을 100으로 지정

    Text("엄")      
        .background(.red)
        .font(.system(size: 40))

    Spacer() 

    Text("준")
        .background(.yellow)
        .font(.system(size: 40))

    Spacer()

    Text("식")
        .background(.blue)
        .font(.system(size: 40))

    Spacer()
}
```
첫번째 Spacer에 minLength의 값을 100으로 설정하면 이때 설정하는 값은 

"Spacer가 가지는 여백의 최소 보장되는 크기"이다.

따라서 Spacer의 여백이 100보단 클 경우엔 무시된다.

---

## frame modifier를 이용하여 Spacer 여백의 크기를 지정

만약 유동적인 Spacer의 여백을 직접 지정하고 싶다면

Spacer에 frame modifier를 호출하면 지정된 크기의 여백을 줄 수 있다.
