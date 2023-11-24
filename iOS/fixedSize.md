# 231121-1 / SWIFT / fixedSize

fixedSize는 뷰를 가장 이상적인 크기로 만들어 준다.

```swift
struct FixedSizeView: View {
    var body: some View {
        HStack {
            Text("🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖🤖")
                .padding()
                .frame(maxHeight: .infinity)
                .background(Color.blue)
            Text("🤖🤖🤖🤖🤖🤖🤖🤖")
                .padding()
                .frame(maxHeight: .infinity)
                .background(Color.green)
            Text("🤖🤖🤖🤖")
                .padding()
                .frame(maxHeight: .infinity)
                .background(Color.red)
        }
    }
}
```

이런 것들에 fixedSize를 붙여주면, 뷰의 크기를 깔끔하게 조정해준다.