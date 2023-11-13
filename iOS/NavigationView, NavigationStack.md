# 230817-1 / SWIFT / NavigationView와 NavigationStack

## NavigationView

네비게이션 뷰는 기존에 사용하던 방법인데 

```swift
var body: some View {
    NavigationView {
        NavigationLink {
            뷰(color: .red, order: 1)
        } label: {
            Text("타이틀")
        }
    }
}
```

NavigationLink를 이용해 타이틀과 뷰를 넣어주는 식으로 사용됬다면

새로운 버전으로는 뷰 대신에 값을 전달한다.

---

## NavigationStack

```swift
var body: some View {
    NavigationStack {
        NavigationLink(value: Color.brown) {
            뷰(color: .orange, order: 2)
        }
        .navigationDestination(for: Color.self) { color in
            뷰(color: color, order: 3)
        }
    }
}
```

NavigationStack 을 사용하게 되면 항상 NavigationLink 와

.navigationDestination(for: ) 수정자는 같이 사용된다고 생각하면 된다.

Stack 은 항상 가장 최근에 추가한 View 를 보여주며 Root View 는 제거되지 않은 특징을 갖고 있다.

### - NavigationLink

NavigationLink 는 기존의 NavigationView 에서 사용할 때 처럼 내가 눌렀을 때 원하는 View 가 나오는 역할을 하게 된다.

하지만 NavigationLink 만 있다고 해서 다음 View로 넘어가지는 않고 새로 만들어진 .

navigationDestination(for: ) 수정자를 사용해야 한다.

### - navigationDestination

.navigationDestination(for: ) 는 특정 종류의 데이터를 제공할 때 Stack 이 가리키는 View 를 보여주게 된다.

즉, View 를 데이터 유형과 연결하게 되고 동일한 종류의 데이터 인스턴스를 제공하는 NavigationLink 를 초기화 하게된다.

