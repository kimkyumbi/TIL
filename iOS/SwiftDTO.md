# DTO

### DTO란? 

DTO는 데이터를 전송하기 위한 객체이다. 

DTO는 getter와 setter를 둘 다 가지고 있다.

또한 가변성이 있어 수정을 할 수 있다.

코드의 의존도 최소화를 위해 쓰기도 한다.

```swift
// EX

public struct RequestDTO: Encodable {
    public let number: Int
    public let name: String

    public init(
        number: Int,
        name: String
    ) {
        self.number = number
        self.name = name
    }
}
```
