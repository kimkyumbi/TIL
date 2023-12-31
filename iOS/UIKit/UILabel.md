# UIKit - UILabel 

UILabel은 텍스트를 쓸 수 있게 해주는 UI이다.

```swift
var TestLabel: UILabel = {
    let label = UILabel()
    label.text = "UILabel"
    label.translatesAutoresizingMaskIntoConstraints = false
    label.textAlignment = .center
    label.backgroundColor = .systemBackground
    return label
}()
```

label.text로 뷰에 나타날 text를 설정할 수 있다.

label.textAlignment로 정렬 기준을 정할 수 있다. 

label.translatesAutoresizingMaskIntoConstraints = false로 직접 위치를 정할 수 있다.