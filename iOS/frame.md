# 230809-1 / SWIFT / frame

### frame이란 
- 컴포넌트의 사이즈를 잡아주는 것(너비, 높이, 정렬)

```swift
Image(systemName: "bolt")
    .resizable()
    .aspectRatio(contentMode: .fit)
    .frame(width: 300, height: 200, alignment: .trailing)
```

.frame을 통하여 너비, 높이, 정령방식을 정해주면 

![Alt text](<../사진/스크린샷 2023-08-09 오후 11.47.21.png>)

이렇게 보이게 되는 것이다.