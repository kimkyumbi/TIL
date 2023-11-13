# 231020-1 / SWIFT / dismiss

dismiss의 사용법은 매우 간단하다고 할 수 있다. 

@Environment 프로퍼티 래퍼로 

`@Environment(\.dismiss) private var dismiss` 이 형식대로 dismiss를 써주고, 

그냥 `dismiss()` 를 이용해 사용할 수 있다.

아래 코드를 보면, 원래 fullScreenCover는 이전 뷰로 돌아갈 수 없다. 

하지만 버튼을 추가해 이전으로 돌아가게 할 수 있는데, 

그냥 버튼을 만들 수도 있겠지만, 

`dismiss()` 를 사용해 더 쉽고 간단하게 만들 수 있다.

```swift
struct dismissView: View {
    
    @Environment(\.dismiss) private var dismiss
    
    var body: some View {
        Button {
            dismiss()
        } label: {
            Text("돌아가기")
        }
    }
}

struct SwiftUIStudy: View {
    
    @State var isThisSheet: Bool = false
    @State var isThisFullScreenCover: Bool = false
    
    var body: some View {
        VStack {
        
            Button {
                self.isThisFullScreenCover.toggle()
            } label: {
                Text("풀 스크린 커버")
            }
            .fullScreenCover(isPresented: $isThisFullScreenCover) {
                dismissView()
            }
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333440077832295/1164714836438040627/2023-10-20_9.00.48.png?ex=65443838&is=6531c338&hm=565b07778710192893906ffcff51d4ee0c1ded51a83a85ab8db5dc6968cf99f0&)

dismiss를 사용해 만든 돌아가기 버튼을 클릭하면 이전 뷰로 돌아가게 된다.