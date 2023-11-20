# 230919-1 / SWIFT / Alert

Alert는 일반적으로 경고 메세지를 보내는 팝업창 용도로 많이 이용한다. 사전 의미도 경보고, 무언가 알리고 싶을 때 SwiftUI에서 이용할 수 있는 뷰다.

```swift
struct AlertView: View {
    
    @State private var isAlert = false
    
    var body: some View {
        Button("Hi there!😄") {
            isAlert.toggle()
        }
        .alert(isPresented: $isAlert) {
            Alert(title: Text("Hello Massage"), message: Text("Hello!!😁"),
                  dismissButton: .default(Text("Hi!👀")))
        }
    }
}
```

Button으로 alert를 보여지게 해 줄 토글을 만들고, 버튼을 눌렀을 때, Alert문이 출력된다. 

![image](<../사진/스크린샷 2023-09-19 오후 10.51.43.png>)

![image](https://file%252B.vscode-resource.vscode-cdn.net/Users/mac/Desktop/All-Github/TIL/%25E1%2584%2589%25E1%2585%25A1%25E1%2584%258C%25E1%2585%25B5%25E1%2586%25AB/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202023-09-19%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.51.43.png)