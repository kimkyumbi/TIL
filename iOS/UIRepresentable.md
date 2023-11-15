# 231115-1 / SWIFT / UIRepresentable

SwiftUI에서 UIKit을 사용할 수 있다.

UIRepresentable은 swiftui에서 uikit을 사용할 수 있게 해 주는 프로토콜이다.

UIRepresentable에는 크게 두 가지 종류가 있는데, 각각 `UIViewRepresentable`, `UIViewControllerRepresentable` 두 가지가 있다.

사용을 할 때는 

```swift
struct DemoView: UIViewRepresentable {
    
}
```

이런식으로 구조체로 선언을 해 준다.

이 때 UIViewRepresentable에는 

```swift
makeUIView(context:) -> UIView

updateUIView(:context:)
```

이 두가지를 정의해주어야 하는데, 각각의 역할은 

makeUIView(context:) -> UIView

    UIView를 생성하는 메소드로, SwiftUI의 View 라이프 사이클동안 "한번" 호출된다. 
    래핑하고자 하는 UIView를 여기서 생성해서 리턴해주면 된다.
    여기서 생성한 UIView를 UIViewRepresentable로 래핑하여 SwiftUI의 View가 된다.

updateUIView(:context:) 

    SwiftUI View의 state가 바뀔때마다 트리거된다고 한다.
    이 메소드 안에서 view의 정보를 업데이트 할 수 있다. 
    또한, @Binding기능을 이용해서 SwiftUI view의 상태도 가져올 수 있다! 
    단, read only이다.

```swift
// 형식
struct Demo: UIViewRepresentable {
    func makeUIView(context: Context) -> DemoView {
        DemoView()
    }
    
    func updateUIView(_ uiView: DemoView, context: Context) {
        
    }
}
```

makeUIView 함수 내에서 생성되는 view의 여러가지 프로퍼티들을 지정해 줄 수 있다. 

원하는 뷰를 생성하고 리턴해주기만 하면 된다.

또한, updateUIView에서는 해당 예제에서 Binding 변수를 이용해서 swfitUI로부터 감지한 상태 변화를 이용하여 Indicator를 start/stopt시킨다.

이제 swiftui에서 써보자.

```swift
struct ContentView: View {
    @State var isAnimating: Bool = false
    
    var body: some View {
        VStack {
            ActivityIndicator(isAnimating: $isAnimating)
            Button(action: { self.isAnimating = !self.isAnimating },
                   label: { Text("show/hide")
                    .foregroundColor(Color.white)
            })
                .background(Color.black)
        }
    }
}
```
클릭 전

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1174244150741303336/2023-11-15_4.06.40.png?ex=6566e315&is=65546e15&hm=bd287f9fd6b65a02e1ed33598e6df6903dcc18fe48b4002f8c9899a72e92b0c2&)

클릭 후

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1174244150485463123/2023-11-15_4.06.45.png?ex=6566e315&is=65546e15&hm=398feef9ec4e74b813ddea7b7a0bc7efeb93fb5c79838a6b1a518ed234316844&)
