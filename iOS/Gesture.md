# 231113-1 / SWIFT / Gesture

모든 `SwiftUi View`에는 `Gesture`인식기가 연결될 수 있으며, 이러한 `Gesture`인식기는 인식기가 활성화 될 때 실행될 클로저를 차례로 연결할 수 있습니다.

## TapGesture 

Tap을 하였을 때 연결된 onEnded 클로저를 실행한다. 

### Ex)
```swift
struct GestureView: View {
    @State private var scale: CGFloat = 1.0
    
    var body: some View {
        Image(systemName: "bolt")
            .scaleEffect(scale)
            .gesture(
                TapGesture()
                    .onEnded { _ in
                        scale += 0.1
                    }
            )
    }
}
```

이렇게 되면 번개 모양을 탭할 때마다 scale이 0.1씩 커지는 것을 불 수 있다.

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173546923421077585/2023-11-13_5.55.33.png?ex=656459bd&is=6551e4bd&hm=2d9084b60b1788271d155602c6eb484299ac6455b2f66bac6ad9461993cfec9b&)

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173546923777589258/2023-11-13_5.55.43.png?ex=656459be&is=6551e4be&hm=71d17a3923175770ac0ad5bcfdaf2857aa73e96891a4872ea9b3ab58f7938aaf&)

## LongPressGesture

사용자가 일정 시간 이상 View를 누르고 있으면 Gesture가 살행됩니다.

### Ex)
```swift
struct GestureView: View {
    @State private var scale: CGFloat = 1.0

    var body: some View {
        Image(systemName: "bolt")
            .scaleEffect(scale)
            .gesture(
                LongPressGesture(minimumDuration: 1)
                    .onEnded { _ in
                        scale *= 2
                    }
            )
    }
}
```
![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173553830286331944/2023-11-13_6.23.30.png?ex=6564602c&is=6551eb2c&hm=2bc66f48b0a72c38a0c9ca577b28b6a5238dd3b9d1b0dd5fda619bc60f7ea362&)

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173553830076629052/2023-11-13_6.23.35.png?ex=6564602c&is=6551eb2c&hm=d69e2915947562d2030ed51d6525307583211f885a6b5a204922faca93ce6630&)

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173553829850140682/2023-11-13_6.23.43.png?ex=6564602c&is=6551eb2c&hm=0b8af20d07ec9d6a5a82e1c6c3095955a2d66334ccb6b49c7303aac4e6ad8585&)

이렇게 1초 동안 Tap을 하고 있으면 두배가 되는 것을 볼 수 있다.

## DragGesture 

offset()뷰의 자연스러운 위치를 조정할 수 있는 수정 자 와 결합할 때 특히 좋습니다.

예를 들어 다음 dragOffset은 드래그 동작에 연결된 크기를 사용하여 이미지를 오프셋 합니다.

이미지를 드래그한 뒤, 손을 떼면 원래 위치로 이동됩니다.

### Ex)
```swift
struct GestureView: View {
    @State private var dragOffset = CGSize.zero
 
    var body: some View {
        VStack {
            Image(systemName: "bolt")
                .resizable()
                .scaledToFit()
                .offset(dragOffset)
                .gesture(
                    DragGesture()
                        .onChanged { gesture in
                            dragOffset = gesture.translation
                        }
                        .onEnded { gesture in
                            dragOffset = .zero
                        }
                )
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173564497512910858/2023-11-13_7.06.13.png?ex=65646a1b&is=6551f51b&hm=83c442afdb438967b8012728a962f53c6fdf31419e1d5592392531ed1c42d744&)

드래그를 할 수 있다.

## MagnificationGesture (확대 / 축소)

MagnificationGesture에는 onChanged 옵션과 onEnded 옵션이 포함되어있습니다.

MagnificationGesture를 뷰에 연결해 줌인, 줌아웃으로 뷰의 크기를 늘리거나 줄일 수 있습니다.

그러기 위해서는 @StatescaleAmount를 저장하는 두개의 속성을 생성, 

scaleEffect() 수정자 내부에 이것을 사용해 다음과 같이 제스처에서 값을 설정해 수행 할 수 있습니다.

### Ex)
```swift
struct MagnificationGestureViews: View {
    @State var currentAmount: CGFloat = 0
    @State var lastAmount: CGFloat = 1
    var body: some View {
        Text("MagnificationGesture")
            .font(Font.title.bold())
            .foregroundColor(.white)
            .padding(50)
            .background(Color.blue.cornerRadius(20))
            .scaleEffect(currentAmount + lastAmount)
            .gesture(
                MagnificationGesture()
                    .onChanged { value in
                        currentAmount = value - 1
                    }
            )
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1173565540011348060/2023-11-13_7.10.22.png?ex=65646b14&is=6551f614&hm=590ab5d7d282fc087f12d5724866b417050843e0a6697c565f9908eda0bdba1f&)

확대 / 축소를 할 수 있다.