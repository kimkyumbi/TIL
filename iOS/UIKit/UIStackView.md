# UIKit - UIStackView 

UIStackView는 이름에 들어간 Stack이라는 단어처럼 View를 Stack처럼 쌓게 해주는 View이다.

```swift
 var inputStackView: UIStackView = {
    let stackView = UIStackView()
    stackView.axis = .horizontal
    return stackView
}()
```

위 코드처럼 UIStackView를 선언한다. 

stackView.axis 의 .horizontal이나 .vertical등을 통해서 View들을 세로로 쌓는 기준을 정할 수 있다. 

