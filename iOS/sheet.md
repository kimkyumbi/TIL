# 230821-1 / SWIFT / sheet(Modal) 

```swift
struct Day8: View {
    
    @State var isShowingModal: Bool = false  // 상태를 바꾸어 준다. (새로운 화면 그려짐)
    
    var body: some View {
        Button {
            isShowingModal = true // 버튼을 눌렀을 때 true
        } label: {
            Text("뭔가 수상한 텍스트다. 클릭해보자. ") // 버튼 이름
        }
        .sheet(isPresented: $isShowingModal) {
            Text("아무것도 없다.. 나가자.")
        }
    }
}
```

버튼을 이용해 눌러졌을 때 새로운 화면으로 넘어갈 수 있게 해 준다.

.sheet(isPresented: , content: )에 Binding변수를 넣고 content에 content를 넣으면 된다.

이제 버튼을 눌렀을 때 isShowingModal이 true가 되면서 Modal창이 띄워지게 된다.

![Alt text](<../사진/스크린샷 2023-08-21 오후 5.49.49.png>)

---

![Alt text](<../사진/스크린샷 2023-08-21 오후 5.48.31.png>)