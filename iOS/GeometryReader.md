# 230911-1 / SWIFT / GeometryReader

우리가 View를 구성할 때 VStack, HStack, ZStack만 적절히 섞어 사용해도 그럴듯한 화면을 만들 수 있다.

하지만 그 이상으로 하위 뷰들의 위치나 모양을 조절해야하는 상황이 생기기도 한다. 

그럴 때는 어떻게 해야 할까?

## GeometryReader

VStack과 HStack같은 ViewBuilder에 적당히 하위 뷰들을 넣어두기만 하면 세세한 설정 없이도 화면에 그럴듯하게 띄워준다.

그 이유는 상위 뷰, 즉 __부모 뷰__ 가 하위 뷰인 __자식 뷰__ 의 위치와 크기를 __제안__ 하기 때문이다.

자식 뷰에 별다른 설정이 들어가지 않는다면 부모 뷰에서 제안한 대로 크기와 모양을 맞추게 된다. 

하지만 부모 뷰에서 제안한 자리가 마음에 들지 않는다면, 부모 뷰의 제안을 무시하고 자신이 직접 위치를 정할 수 있다.

그러니까, 부모 뷰는 제안만 할 뿐 자식 뷰의 자리를 __강제__ 할 수 없다는 것이다. 

이때, 자식 뷰는 부모 뷰가 제안한 위치 내에서 자신이 원하는 자리를 찾아갈 수 있는데, 이를 위해 사용되는 것이

#### GeometryReader 이다.

- 하지만 여기서 주의해야 하는 점은, 자식 뷰는 부모 뷰가 제안한 위치 내에서만 이동할 수 있고, <br>
  부모 뷰가 제안한 위치를 벗어나는 곳으로는 갈 수 없다.

### GeometryReader ?

먼저 애플 공식 문서에 따르면, 

> A container view that defines its content as a function of its own size and coordinate space.

GeometryReader는 그 자체로 __View__ 이며, container 안 View 스스로의 크기와 위치를 함수로 정의한다고 소개되어있다.

#### 예제를 보도록 하자.

```swift
struct Day19: View {
    var body: some View {
        VStack {
            Text("GeometryReader")
            DAY19()
        }
    }
}

struct DAY19: View {
    var body: some View {
        Circle()
            .foregroundColor(.blue)
    }
}
```

DAY19는 파란색 원을 생성하는 뷰이고, Day19는 GeometryReader라는 텍스트와 DAY19를 호출하는 뷰이고,

![Alt text](<../사진/스크린샷 2023-09-11 오후 11.03.52.png>)

이렇게 나오게 된다. 

하지만 이 원의 위치가 맘에 들지 않으니 바꾸고 싶다. 

자, 이제 GeometryReader를 써보자. 

아래 코드를 보면,

```swift
struct DAY19: View {
    var body: some View {
        GeometryReader { geometry in
            Rectangle()
                .path(in: CGRect(x: geometry.size.width / 2, 
                y: 0, width: geometry.size.width / 2.0,
                height: geometry.size.height / 2.0))
                .fill(Color.blue)
        }
    }
}
```

GeometryReader를 사용해 VStack이 제안한 크기와 위치에 접근할 수 있어, 

VStack이 제안한 높이, 너비를 geometry.size.width와 geometry.size.height로 접근했다. 

이에 접근해 width와 height를 반으로 깎고, 위치는 VStack에서 제안한 너비의 절반 위치로 옮겼다.

![Alt text](<../사진/스크린샷 2023-09-11 오후 11.03.22.png>)
