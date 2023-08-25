# 230825-1 / SWIFT / Group

일반적으로 VStack, HStack, ZStack은 View들을 쌓아준다. 

하지만 이 스택들이 쌓을 수 있는 View의 개수가 존재하는데, 10개이다.

그래서 그것들을 모아줄 수 있는 것이 바로 Group이다. 

예를 들어,

```swift
struct Day12: View {
    var body: some View {
        VStack {
            Text("1")
            Text("2")
            Text("3")
            Text("4")
            Text("5")
            Text("6")
            Text("7")
            Text("8")
            Text("9")
            Text("10")
            Text("11")
        }
    }
}
```

이렇게 Text를 11개 넣게 되면 10까지만 나오고 11은 나오지 않지만,

```swift
struct Day12: View {
    var body: some View {
        VStack {
            Group {
                Text("1")
                Text("2")
                Text("3")
                Text("4")
                Text("5")
            }
                Text("6")
                Text("7")
                Text("8")
                Text("9")
                Text("10")
                Text("11")
        }
    }
}
```

위 코드처럼 중간지점을 Group으로 묶어주면 1부터 11까지 매우 정상적으로 나오는 것을 확인할 수 있다. 
