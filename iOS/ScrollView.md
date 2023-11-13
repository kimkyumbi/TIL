# 230804-1/ SWIFT / ScrollView

`ScrollView` 는 이름 그대로 스크롤을 할 수 있게 만들어준다. 

화면을 넘어가는 스택을 쌓았을 경우 활용할 수 있다. 

기본적으로 스크롤바는 활성화되어있기 때문에 `showIndicators` 를 `false` 로 설정하여 스크롤 바를 없앨 수도 있다.

```swift
ScrollView(showsIndicators: false) {
     // horizontal 은 좌우 스크롤
     //showIndicators: false = 스크롤바 없애기
    Text("1")
        .frame(width: 300, height: 500)
        .background(.red)
    Text("2")
        .frame(width: 300, height: 500)
        .background(.blue)
    Text("3")
        .frame(width: 300, height: 500)
        .background(.yellow)
}
```

