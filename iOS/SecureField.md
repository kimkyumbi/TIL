# 230815-1 / SWIFT / SecureField

우리는 일상생활에서 비밀번호를 매우 많이 사용한다. 

그 비밀번호를 SecureField로 사용할 수 있다.

```swift
struct Day6: View {
    
    @State var myPassword: String = ""
    @State var isSecureMode: Bool = true
    
    var body: some View {
        VStack {
            Text(myPassword)
            if isSecureMode {
                SecureField("Password", text: $myPassword)
                    .textFieldStyle(.roundedBorder)
            } else {
                TextField("Password", text: $myPassword)
                    .textFieldStyle(.roundedBorder)
            }
            
            Button {
                isSecureMode.toggle()
            } label: {
                Text("Change")
            }
        }
        
    }
}
```

위 코드는 아래 사진처럼 보이게 된다.

![Alt text](<../사진/스크린샷 2023-08-15 오후 11.33.51.png>)

이렇게 비밀번호를 입력한다면 가려줄 수 있고, 

Change버튼을 통해

![Alt text](<../사진/스크린샷 2023-08-15 오후 11.34.00.png>)

이렇게 자신이 쓴 비밀번호를 볼 수도 있다.