# 230828-1 / SWIFT / @State +

```swift
struct State1: View {
    
    // 항상 최신의 값을 저장할 수 있게 바로바로 업데이트 되도록 명시해 놓은 것
    @State var number : Int = 26 
    
    var body: some View {
        VStack {
            Text("Number 는 \(number)")
                .padding(.bottom, 20)
            
            Button {
                number += 26 // 버튼을 누르면 number 값에 26을 더하고 최신의 값은 52 저장 후 업데이트 
            } label: {
                Text("나는 더하기 단추") // 나는 더하기 단추
                    .fontWeight(.bold)
                    .padding(10)
            }
        }
    }
}
```

![Alt text](<../사진/스크린샷 2023-08-28 오후 11.25.21.png>)

이렇게 초기값인 26에서 나는 더하기 단추를 누를 때마다 26씩 더해진다. 

![Alt text](<../사진/스크린샷 2023-08-28 오후 11.25.30.png>)
