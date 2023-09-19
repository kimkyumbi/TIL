# 230909-1 / SWIFT / LazyGrid - VGrid

LazyStack과 비슷하게 LazyGrid의 Lazy도 스크린(사용자가 보는화면)에 무언가를 랜더링할 필요가 있을 때까지는 구성하지 않는다는 뜻이다. 

## Grid

그렇다면 `Grid`는 뭘까?

Grid는 horizontal Direction으로 사진을 배열하여 화면을 구성하기 좋다.

__LazyGrid는 columns를 사용하여 반드시 GridItem이라는 매개변수를 같은 변수를 생성해줘야 한다.__

이 GridItem은 초기화 시 넘겨줄 수 있는 파라미터로 alignment(정렬 방법), spacing(item 간격), size(크기)가 있다.

여기서 우선 size를 보면 GridItem.Size라고 Size enum 타입으로 케이스가 선언되어 있다.

총 3개의 케이스가 있다.
 
---

### adaptive(minumum: CGFloat, maximum: CGFloat)

최소값과 최대값을 정하고 이 사이의 사이즈로 가장 많이 배치 가능하게 할때 사용한다.

---

### flexible(minimum: CGFloat, maximum: CGFloat)

최소/최대값을 정해두고 뷰 크기에 따라 사이즈를 조절할 수 있다.

인자에 아무것도 주어지지 않는다면 해당 뷰의 크기를 아이템의 수로 나눠 계산해 그려준다.

---

### fixed(CGFloat)

고정된 사이즈로 아이템을 지정해준다.

---

그 다음으로 spacing을 통해 각 아이템 사이 간격을 줄 수 있다.

그럼 예제를 보자.

```swift
struct Day17: View {
    
    
    let columns = [GridItem(.flexible()), GridItem(.flexible())] 
    let colors: [Color] = [.black, .blue, .brown, .cyan, .gray,
                           .indigo, .mint, .yellow, .orange, .purple]

    var body: some View {
        LazyVGrid(columns: columns) {
            ForEach(colors, id: \.self) { color in
                RoundedRectangle(cornerRadius: 10)
                .frame(width: 150, height: 100)
                .foregroundColor(color)
            }
        }
        .padding()
    }
}
```

![Alt text](<../사진/스크린샷 2023-09-09 오후 7.41.38.png>)

이렇게 flexible을 두개 만들어 2열까지만 나타나고 행으로 쭉 쌓이게 된다.