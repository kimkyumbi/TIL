# 230727-1 / SWIFT / MVVM(Model, View, ViewModel)

## Model

Model은 MVC에서의 Model과 마찬가지로 데이터와 관련된 코드를 담고 있다. 

데이터를 담아두기 위한 구조체들은 물론, 네트워크 로직, JSON 파싱 코드를 담고 있다.

```swift
struct Person {
  let name: String
  var age: Int
  init(json: JSON) {
    name = json["name"].stringValue
    age = json["age"].intValue
  }
}
```
```
이런 식으로 Person에 대한 데이터를 담을 수 있는 구조체를 만들고, 네트워크를 통해 JSON 정보를 받았을 때 이를 이용해 구조체에 파싱까지 할 수 있는 init 함수까지 포함할 수 있다. 전형적인 Model 계층에 해당하는 파일이라고 볼 수 있다. (위 JSON 파싱 방식은 SwiftyJSON 라이브러리를 사용한 경우다.)

Model은 View, ViewModel 계층을 전혀 신경쓰지 않아도 된다. 데이터를 어떻게 가지고 있을 지만 생각하면 되고, 그 이상의 비즈니스 로직이나 View에서 프로퍼티들을 어떻게 보여주는지에 굳이 맞출 필요는 없다.
```

## View


View는 앱의 UI에 대한 코드를 담고 있는 계층이다. 

View의 각 컴포넌트에 대한 정보를 담고, 어느 위치에 어떻게 배치될지 작성되어있다. 

View는 디자인적인 요소도 있지만, ViewModel로부터 데이터를 가져와 어떻게 배치할지, 

특정 상황에 따라 ViewModel의 어떤 메서드를 이용할지에 대해서도 가지고 있다.

MVC와 마찬가지로 View는 재사용성이 강조되며, 컴포넌트를 적당히 잘 나누어 중복된 코드를 줄이는 것이 중요하다.

```swift
struct ContentView: View {
  let personList: [Person] = [Person(name: "Lee", age: 23), Person(name: "Jeon", age: 28)]
  
  var body: some View {
    ScrollView {
      ForEach(personList, id: ./self) { person in
        PersonListItemView(person: person)
      }
    }
  }
}
struct PersonListItemView: View {
  let person: Person
  
  var body: some View {
    VStack(alignment: .leading) {
      Text("Name: \(person.name)")
      Text("Age: \(person.age)")
    }
      .padding(16)
  }
}
```

```
View는 이런 식으로 재사용할 수 있는 View를 따로 만들어 같은 코드를 여러번 작성하지 않고 재사용성을 살릴 수 있다. 위 코드는 SwiftUI로 UI를 구성한 경우로, 각 컴포넌트들이 어떻게 배치될지 코드를 통해 짐작할 수 있다.

하지만 이 예시 코드에서는 간단하게 보여주기 위해 ViewModel을 사용하지 않고 Model 계층을 직접 정의했는데, 사실은 MVVM 패턴에서 View는 Model을 직접 소유하지 않아야 한다. ViewModel로부터 받아와서 View에 정보를 집어넣어주는 방식이 일반적이다.
```

## ViewModel

```
ViewModel은 앱의 핵심적인 비즈니스 로직을 담고 있는 코드의 계층이다. MVC 패턴의 Controller와 비슷한 역할을 하고 있다. View와 Model의 사이에서 View의 요청에 따라 로직을 실행하고, Model의 변화에 따라 View를 refresh하는 등, 유사한 점이 아주 많다.

Model에 뭔가 변화가 생기면 View에게 notification을 보내주는 역할을 한다. 또한, View로부터 전달받는 요청을 해결할 비즈니스 로직들을 담고 있다. ViewModel은 UI 관련 코드로부터 완전히 분리되어있고, 따라서 ViewModel 파일에는 SwiftUI같은 UI 프레임워크를 import할 이유조차 없다.
```
