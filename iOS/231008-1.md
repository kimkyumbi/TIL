# 231008-1 / SWIFT / @ObservedObject

ObservedObject는 프로퍼티 래퍼이다. 

ObservableObject 타입에서 해당된다.

ObservableObject를 구독하며 값 업데이트가 발생하면 뷰를 갱신해준다.

예제를 보자.

```swift
class User: ObservableObject {
    @Published var age = 10
}

struct MainView: View {
    @StateObject var green = User()
  
    var body: some View {
        Text("Age is \(green.age)")
        SubView(user: green)
    }
}

struct SubView: View {
    @ObservedObject var user: User

    var body: some View {
        Button("Plus Age") {
            user.age += 1
        }
    }
}
```

SubView에 @ObesrvedObject로 User 클래스 타입으로 프로퍼티를 지정해준다.

해당 클래스에서는 변수 age가 @Published로 지정되어 있다.

SubView에는 버튼이 있어 클릭 시 age의 값을 변경해준다.

MainView에서는 해당 User 타입을 참조하여 프로퍼티를 만든다.

SubView에 해당 프로퍼티를 넘겨주어 연결해준다.

