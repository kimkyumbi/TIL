# 230827-1 / SWIFT / Animation

애니메이션은 움직임을 넣어줄 수 있다. 

```swift
struct Day12: View {
    
    @State var isLighting: Bool = false
    
    var body: some View {
        VStack {
            Image(systemName: "cloud")
                .offset(y: -200)
            HStack {
                Image(systemName: "bolt")
                    .rotationEffect(isLighting ? .degrees(0) : .degrees(180+360))
                    .offset(y: isLighting ? 0 : -200)
                    .padding()
                    .animation(.easeInOut(duration: 5), value: isLighting)
                Image(systemName: "bolt")
                    .offset(y: isLighting ? 0 : -200)
                    .padding()
                    .animation(.easeInOut(duration: 5), value: isLighting)
            }
            Button {
                isLighting.toggle()
            } label: {
                Text("Click")
            }
        }
    }
}
```

offset을 이용해 bolt 이미지의 위치를 움직일 수 있다. 

click을 누르면 isLighting이 false에서 true가 되어 움직일 수 있는 것이다. 

![Alt text](<../사진/스크린샷 2023-08-27 오후 10.32.18.png>)

처음 화면을 보면 번개가 위에 있는것을 알 수 있다. 

아래 클릭버튼을 누르게 되면 움직인다. 

![Alt text](<../사진/스크린샷 2023-08-27 오후 10.32.55.png>)

왼쪽 번개는 degrees를 이용해 회전하게 만들었다. 

오른쪽 번개는 회전하지 않고 일직선으로 움직인다. 

![Alt text](<../사진/스크린샷 2023-08-27 오후 10.33.01.png>)
