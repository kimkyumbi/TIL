# 230904-1 / SWIFT / @FocusState와 TextField

`Focus` 를 자유롭게 이동시키기 위한 프로퍼티 래퍼이다.

아래와 같이 선언해 사용한다. 

```swift
@FocusState var isFocusField: Bool
@State var email: String

TextField("email", text: $email, prompt: Text("email"))
	.focus($isFocusField)
```

`Focus` 할 창이 여러 개 있는 경우에는 enum으로 선언이 가능하다.

```swift
enum FocusableField: Hashable {
    case email
    case password
}

@FocusState var focus: FocusableField?

TextField(email, text: $email, prompt: Text("email"))
	.focused($focus, equals: .email)
TextField(password, text: $password, prompt: Text("password"))
	.focused($focus, equals: .password)
```
