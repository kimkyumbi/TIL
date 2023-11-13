# 230807-1 / SWIFT / List(Section)
```swift
List {
    HStack {
        Image(systemName: "circle.fill")
        Text("a")
    }
    HStack {
        Image(systemName: "heart.fill")
        Text("c")
    }
    HStack {
        Image(systemName: "star.fill")
        Text("c")
    }
}
```
위의 그냥 리스트에 Section을 추가했다.

```swift
List {
    Section {
        HStack {
            Image(systemName: "circle.fill")
                Text("a")
        }
        HStack {
            Image(systemName: "heart.fill")
            Text("c")
        }
        HStack {
            Image(systemName: "star.fill")
            Text("c")
        }
    } header: {
        Text("gyeombi")
    } footer: {
        Text("kyumbi")
    }
}
```

Section에는 header와 footer가 있는데 

header는 한 section 위에 종류 등을 추가하는 것이고

footer는 한 section 아레에 종류 등을 추가하는 것이다. 

![Alt text](<../사진/스크린샷 2023-08-07 오후 11.03.42.png>)

header에 들어간 영어는 대문자로 바뀐다.