# UIKit - Then 라이브러리 

then 라이브러리는

원래 우리가 쓰던 

```swift
let label: UILabel = {
  let label = UILabel()
  label.textAlignment = .center
  label.textColor = .black
  label.text = "Hello, World!"
  return label
}() 
```

이런 코드를 

```swift
let label = UILabel().then {
  $0.textAlignment = .center
  $0.textColor = .black
  $0.text = "Hello, World!"
}
```

이렇게 코드를 단순하고 깔끔하게 만들어 준다. 
