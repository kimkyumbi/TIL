# 231102-1 / SWIFT / ViewModifier

ViewNodifier는 View나 다른 ViewModifier에 기존 버전과 다른 버전을 생성하는 프로토콜이다.

간단하게 생각하면 커스텀 Modifier를 만들 수 있는 프로토콜이라고 생각하면 된다.

ViewModifier은 ViewModifier 프로토콜을 채택해야 하는데, 

ViewModifier은 body가 있어야 한다.

```swift
// body는 이러한 형식으로 되어 있다.
func body(content: Content) -> some View {
          
}
```

이후에 some View 타입으로 반환을 해주어야 하는데, (content: Content) 부분이 Modifier에 저장된 View를 불러오는 역할을 한다.

```swift
struct ViewModifierView: ViewModifier {
    func body(content: Content) -> some View {
        content
            .font(.system(size: 20))
            .background(.green)
    }
}

struct ViewModifierTest: View {
    var body: some View {
        Text("hELLO, wORLD?") ㅜ
        Text("Hello, World!")
            .modifier(ViewModifierView())
    }
}
```

예제 코드를 보자.

구조체 ViewModifierView는 ViewModifier 프로토콜을 채택했다. 

body로 `.font(.system(size: 20))`와 `.background(.green)` 를 작성해주었다.

그리고 ViewModifierTest에서 .modifier를 사용해 ViewModifierView를 적용시키면 

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1169647427565932605/2023-11-02_11.40.41.png?ex=65562a0d&is=6543b50d&hm=4273a3c4215744ac16ca2ed73eca81c9487b22e36c08226fe969f97cdf3c0b09&)

이렇게 작성한 font size와 background를 green이 나오는 것을 볼 수 있다.