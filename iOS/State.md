# 230812-1 / SWIFT / @State

우리가 버튼을 클릭했을때, `"김겸비"`라는 문구가 나오게 하고 싶다면 어떻게 해야 할까?

화면을 다시 그려주어야 한다. 

그때 사용하는 것이 `@State`인데, 

```swift
import SwiftUI

struct ContentView: View {

    @State var name: String = "" 

    var body: some View {
        VStack {
            Text("Hi! gyeombi!")

            Button {
                name = "kyumbi"
            } label: {
                Text("Click")
            }
        }
    }
}
```

이 코드는 `Click` 버튼을 클릭하면 이름이 gyoembi에서 kyumbi로 바뀌는 코드이다.

이때 이름을 바꾸기 위해서 화면을 다시 그려줘야 하는데, 이때 `@State`를 사용하는 것이다.

`@State`가 없다면 구조체 안에 들어있는 변수를 바꿀 수 없기 때문에 오류가 뜨게 된다.