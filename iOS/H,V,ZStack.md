# 230725-3 / SWIFT / HStack, VStack, ZStack

## 정의

내부에 선언된 View들을 Leading에서 Trailing으로 배치한다.

---

## HStack

HStack은 View를 "수평"으로 배치해주는 View이다.(왼쪽에서 오른쪽으로)

```swift
struct ContentView: View {
    var body: some View {
        HStack {
            Text("겸비")
                .background(.red)
            Text("추운 겸비")
                .background(.yello)
            Text("춥고 배고픈 겸비")
                .background(.blue)
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018542423883826/2023-07-25_5.33.32.png?ex=651e5ba2&is=651d0a22&hm=f9e1a833a1899aebbda2b369aabbf3b8850091df19e84f37c7528f81867ff958&)

각각의 Text에는 기본적으로 여백이 있다. 

---

## VStack

VStact은 View를 "수직"으로 배치해주는 View이다.(위에서 아래로)

```swift
struct ContentView: View {
    var body: some View {
        HStack {
            Text("겸비")
                .background(.red)
            Text("추운 겸비")
                .background(.yellow)
            Text("춥고 배고픈 겸비")
                .background(.blue)
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018722044936222/2023-07-25_8.13.01.png?ex=651e5bcc&is=651d0a4c&hm=e09169c4d88050c9d6b0b2ac2861ec99c74105186b50f05c719ef2e9add6be5b&)

---

## ZStack 

ZStack은 View들을 겹쳐서 두 축으로 배치한다.

```swift
struct ContentView: View {
    var body: some View {
        ZStack {
            Text("겸비")
                .background(.red)
            Text("추운 겸비")
                .background(.yellow)
            Text("춥고 배고픈 겸비")
                .background(.blue)
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018722279825449/2023-07-25_8.13.47.png?ex=651e5bcc&is=651d0a4c&hm=c90073f65bdf77e179b0d2762298e84ec232470f008f13c3901329eda17da539&)

각 Text들의 크기를 바꾸어 주면?

```swift
struct ContentView: View {
    var body: some View {
        ZStack {
            Text("겸비")
                .background(.red)
                .font(.system(size: 100))
            Text("추운 겸비")
                .background(.yellow)
                .font(.system(size: 50))
            Text("춥고 배고픈 겸비")
                .background(.blue)
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1159018542675533874/2023-07-25_8.15.04.png?ex=651e5ba2&is=651d0a22&hm=6e835645df7522ce8db62cddde2be60efdb62ed4653a6e3b9e8a1885a0ff6b8f&)

이렇게 가장 먼저 선언된 Text부터 뒤에서부터 배치된 것을 볼 수 있다.

## Stack에서 사용할 만한 modifier
 
### Stack의 크기 변경하기

Stack의 크기는 내부 뷰를 표시하기 위한 최소한의 크기로 표시된다.

내부 뷰의 크기가 다를 경우,

너비 or 폭이 가장 큰 놈에 의해서 프레임이 맞춰진다.

이렇게 `.frame`이라는 modifier를 이용해서 직접 설정해줄 수 있다.

---

### Stack 내의 정렬 방식(alignment) 변경하기

Stack을 생성할 때 파라미터 값으로 alignment를 직접 설정해 줄 수 있다.

trailing / leading / center <- 이 명령어들을 통해 정렬기준을 바꿀 수 있다.

---

### Stack 내의 여백(spacing) 크기 변경하기

Stack 내부 뷰 간격 간의 여백을 지정하는 spacing이란 파라미터의 기본 값은 nil인데,

이때 nil은 0이 아니라 기본 값이다
