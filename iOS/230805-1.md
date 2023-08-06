# 230805-1 / SWIFT / List

List를 만드는 방식에는 정적인 것과 동적인 것 두가지로 나눌 수 있다. 

```swift
List {
    HStack {
        Image(.systemName: "heart")
        Text("Heart")
    }
        HStack {
        Image(.systemName: "star")
        Text("Star")
    }
        HStack {
        Image(.systemName: "circle")
        Text("Circle")
    }
}
```
이렇게 정적으로 작성하기보다 

```swift
struct Person: Identifiable {
    var id = UUID()
    let name: String
    let imageName: String
}

struct ContentView: View {
    var body: some View {
        let people: [Person] = [Person(name: "겸비", imageName: "heart"), 
                                Person(name: "겸비", imageName: "heart"), 
                                Person(name: "겸비", imageName: "heart"),]
        List(people) {person in 
            Text(person.name)
        }
    }
}

```
이렇게 작성하여 조금 더 동적으로 만들어주는것이 좋다. 
