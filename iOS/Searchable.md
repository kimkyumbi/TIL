# 230925-1 / SWIFT / .searchable

.searchable은 말 그대로 검색을 가능하게 해 준다.

```swift
struct Day26: View {
    
    @State private var searchAble: String = ""
    
    var body: some View {
        NavigationStack {
            Text("검색 가능")
                .font(.system(size: 50))
        }.searchable(text: $searchAble, prompt: "검색어를 입력하세요.")
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1155856974009876600/2023-09-25_10.19.18.png)

searchable의 정의를 보면

```swift
func searchable(
    text: Binding<String>,
    placement: SearchFieldPlacement = .automatic,
    prompt: LocalizedStringKey
) -> some View
```

위 처럼 나온다. 

