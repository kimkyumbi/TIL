# 230922-1 / SWIFT / onAppear(), onDisappear

특정 View가 나타날 때 특정 항목을 로드한다.

```swift
struct Day24: View {
    var body: some View {
        NavigationStack {
            VStack {
                NavigationLink(destination: DetailView()) {
                    Text("onAppear(), onDisappear()")
                }
            }
        }
    }
}

struct DetailView: View {
    var body: some View {
        VStack {
            Text("겸B")
        }
        
        .onAppear() {
            print("DetailView onAppear")
        }
        
        .onDisappear() {
            print("DetailView onDisappear")
        }
    }
}
```

NavigationLink로 들어갔을 때 DetailView onAppear이 출력되고,

나올 때는 DetailView onDisappear이 출력된다.