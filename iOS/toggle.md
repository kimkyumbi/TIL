# 230818-1 / SWIFT / Toggle

```swift
struct Day7: View {
    
    @State var isLightOn: Bool = false
    
    var body: some View {
        Toggle(isOn: $isLightOn) {
            if isLightOn {
                Text("Light On")
            } else {
                Text("Light Off")
            }
        }
        .toggleStyle(.switch)
        .tint(.green)
        .padding()
    }
}
```

Toggle은 우리가 쉽게 볼 수 있는 스위치를 끄고 키는 것과 같은 동작을 한다. 

![Alt text](<../사진/스크린샷 2023-08-20 오전 12.07.56.png>)

이렇게 위 코드에서 처럼 isLightOn 이 false이기 때문에 기본 상태는 Light Off 상태이고, 

![Alt text](<../사진/스크린샷 2023-08-20 오전 12.08.03.png>)

스위치를 눌렀을 때 isLightOn이 true로 바뀌며 Light On 상태가 된다.