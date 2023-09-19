# 230829-1 / SWIFT / @Binding 


@Binding은 @State와 많은 연관이 있는데요. 

@State가 상태가 변할 때마다 뷰가 계속해서 렌더링을 해 업데이트를 할 수 있도록 명시해 주는 것이라고 했습니다.

@Binding은 간단하게 생각해서 값을 공유해 주는 것이라고 생각하면 좋습니다. 

아래 코드를 보면 부모뷰와 자식뷰가 있는데요. 

@Binding을 통해 부모뷰에서 값이 바뀌면 자식뷰에도 그대로 값이 바뀌고, 자식뷰에서 값이 바뀌면,

부모뷰에서도 값이 바뀌는 양방향으로 값이 바뀌게 하는 것이죠. 

그래서 아래 코드를 실행하면, 나는 더하기 단추 버튼을 눌렀을 때, 부모뷰와 자식뷰 두 뷰 모드 26이 더해집니다. 

값이 52가 되는 것이죠.

반대로 + 를 클릭했을 때, 부모뷰와 자식 뷰 모두 1이 더해집니다. 

값이 52에서 53이 되는 것입니다. 

```swift
struct State1: View {
    
    @State private var number : Int = 26
    
    var body: some View {
        VStack {
            Text("Number 는 \(number)")
                .padding(.bottom, 20)
            
            Button {
                number += 26
            } label: {
                Text("나는 더하기 단추")
                    .fontWeight(.bold)
                    .padding(10)
            }
            BindView(number: $number)
        }
    }
}

struct BindView: View {
    
    @Binding var number : Int
    
    var body: some View {
        Text("\(number)")
        Text("+")
            .onTapGesture {
                number += 1
                print(number)
            }
    }
}
```

![Alt text](<../사진/스크린샷 2023-08-29 오후 11.18.44.png>)

![Alt text](<../사진/스크린샷 2023-08-29 오후 11.18.52.png>)
