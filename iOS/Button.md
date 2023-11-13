# 230803-1 / SWIFT / Button

버튼은 눌렸을때 동작하는 부분과 어떻게 생겼는지를 꾸미는 부분으로 되어있다.

```swift
Button {
    print("이제 시작이다") // 버튼을 눌렀을 때 출력되는 부분(동작하는 부분)
} label: { //  어떻게 생겼는지를 꾸미는 부분
    Text("드디어 찾았다") // 버튼의 이름
        .padding() // 여백
        .frame(width: 100) // 여백의 크기 지정
        .background(.yellow) // 뒷배경색을 노란색으로 지정
        .cornerRadius(13) // 모서리 부분을 둥글게 해준다.
}
```

![Alt text](<../사진/스크린샷 2023-08-03 오후 1.06.26.png>)

이렇게 버튼의 모양과 여백, 색 등등을 꾸밀 수 있다.

또한 이 버튼을 눌렀을 때 `이제 시작이다` 가 출력되게 해놓았으므로

누른다면 

![Alt text](<../사진/스크린샷 2023-08-03 오후 1.10.03.png>)

이렇게 잘 나온다.

---

```swift
Button("Delete", role: .destructive) { 
    print("Deleted!")
}
```

![Alt text](<../사진/스크린샷 2023-08-03 오후 1.05.11.png>)


이 버튼의 `role` 은 `.destructive` 라는 역할을 지정하는 것 정도로 보면 된다. 

`.destructive` 를 쓰게 된다면 자동으로 빨간색 버튼이 된다. 