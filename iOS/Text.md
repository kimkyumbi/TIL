# 230803-2 / SWIFT / Text
```swift
VStack {
    Text("Hello kyumbi!")
        .bold() // 굵은 글씨
        .italic() // 이탤릭체로 바꿔줌
        .strikethrough() // 글씨 가운데에 줄
    Text("Hello kyumbi!")
        .font(.system(size: 30)) // 글씨 크기 지정
    Text("Hello kyumbi!")
        .underline(true, color: .orange) // 밑줄
        .foregroundColor(.red)
        .background(.purple) // 뒷배경색 지정
    Text("Hello kyumbi!")
        .foregroundColor(.gray) // 글씨 색 지정
        .font(.system(size: 39, weight: .bold, design: .rounded))
            
    }
```

![Alt text](<../사진/스크린샷 2023-08-04 오후 12.32.25.png>)

Text는 위 코드에 나온 것 말고도 꾸밀 수 있는 많은 기능이 있다. 
