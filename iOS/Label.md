# 230822-1 / SWIFT / Label 

```swift
struct Day10: View {
    var body: some View {
        VStack {
            HStack {
                Text(Image(systemName: "bolt"))
                Text("ruaql")
            }
            
            Label("ruaql", systemImage: "bolt")
        }
    }
}
```

위 코드를 실행시키면 아래 사진처럼 화면이 보인다. 하지만 코드를 보면 Text로 각각 써서 만든 것을 Label 하나로 만들었다는 것을 알 수 있다. 이처럼 Label은 글자와 그림을 같이 쓸 때 하나하나 쓰면 힘드니 한번에 쓸 수 있도록 만들어주는 것이다.

![Alt text](<../사진/스크린샷 2023-08-22 오후 6.08.40.png>)
