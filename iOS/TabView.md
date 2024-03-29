# 230813-1 / SWIFT / TabView


탭뷰의 정의는 대화형 사용자 인터페이스 요소를 사용해 여러 하위 뷰 간 전환할 수 있도록 하는 뷰다.

즉 다들 흔히 알고 있는 탭바의 항목들을 클릭해 뷰를 전환할 수 있게 해주는것이다.

```swift
TabView {
    ZStack {
        Color.orange.ignoresSafeArea() // SafeArea 무시, 배경색 orange
        Text("gyeombi")
    }
        .tabItem {
            Label("item1", systemImage: "bolt") // Image와 Text로 나누어 쓸 수도 있다.
        }
    Text("kyumbi")
        .tabItem {
            Label("item2", systemImage: "heart")
        }
}
```

위 코드는 두개의 탭으로 누를때 색깔과 중앙에 나온 Text가 바뀌는 간단한 코드이다.

![Alt text](<../사진/스크린샷 2023-08-13 오후 10.45.52.png>)

이렇게 safearea를 무시하여 끝까지 색을 채운것도 확인할 수 있다.

item2를 누르게 되면

![Alt text](<../사진/스크린샷 2023-08-13 오후 10.46.38.png>)

이렇게 흰색으로 배경이 바뀌며 중앙에 있는 Text도 바뀌는 것을 볼 수 있다.