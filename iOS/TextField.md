# 230814-1 / SWIFT / TextField

TextField는 사용자의 입력을 받을 수 있게 해 준다.

```swift
struct Day5: View {
    
    @State var userID: String = ""
    
    var body: some View {
        VStack(alignment: .leading) {
            Text("ID")
            TextField("Enter your ID", text: $userID)
        }
        .padding()
    }
}
```

위 코드를 작성하면 

![Alt text](<../사진/스크린샷 2023-08-14 오후 11.57.18.png>)

이런 화면이 나오게 되고

![Alt text](<../사진/스크린샷 2023-08-14 오후 11.56.19.png>)

이렇게 입력을 할 수 있다.