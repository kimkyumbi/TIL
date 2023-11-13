# 230822-2 / SWIFT / ProgressView

우리는 로딩화면을 볼 때 보통 동그랗게 돌아가는 로딩화면이나 밑에 바가 100%에 도달하면 실행되는 로딩화면을 많이 봐왔다. ProgressView는 그러한 로딩화면을 구현해주는 View이다. 

아래 코드는 로딩화면 두개를 구현한 것이다. 

```swift
struct Day9: View {
    
    @State var progress: Double = 0 // 바 로딩화면 수 증가를 위한 @State
    
    var body: some View {
        VStack {
            ProgressView() // 동그란 로딩화면
            // 앞쪽부터 차레로 메시지, 초기값, 최종값
            ProgressView("Loading...", value: progress, total: 100) 
            Button {
                progress += 5 // progress + 5 = progress
            } label: {
                Text("click") // click을 클릭했을 때
            }
        }
        .padding()
    }
}
```

실행하면

![Alt text](<../사진/스크린샷 2023-08-22 오후 6.16.58.png>)

이렇게 보이게 된다. 동그란 로딩은 실제로는 돌아간다. 