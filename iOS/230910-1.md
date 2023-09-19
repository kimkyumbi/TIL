# 230910-1 / SWIFT / LazyGrid - HGrid

LazyHGrid는 열은 무수히 증가해 구성될 수 있고 행에 최대 몇개의 View가 담길지는 특정하게 지정할 수 있습니다.

즉 LazyVGrid와 반대다.(colums와 row의 차이로 인식하면 편하다.)

```swift
struct Day18: View {
    
    let rows = [GridItem(.flexible())]
    let colors: [Color] = [.black, .blue, .brown, .cyan, .gray,
                           .indigo, .mint, .yellow, .orange, .purple]
     
     var body: some View {
         ScrollView(.horizontal) {
             LazyHGrid(rows: rows) {
                ForEach(colors, id: \.self) { color in
                    RoundedRectangle(cornerRadius: 10)
                    .frame(width: 50, height: 450)
                    .foregroundColor(color)
                }
            }
        }
        .padding()
     }
}
```

예제를 보면 

![Alt text](<../사진/스크린샷 2023-09-10 오후 7.02.45.png>)

이런식으로 나오는 것을 볼 수 있다.