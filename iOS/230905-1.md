# 230905-1 / SWIFT / Codable

먼저 정의부터 보자.

Codable은 자신을 변환하거나 외부표현(external representation)으로 변환할 수 있는 프로토콜이다.

외부표현은 `JSON`이라고 생각하면 편하다.

Codable은 

```
typealias Codable = Decodable & Encodable
```

이러한 형태로 이루어져 있다. 

---

### Decodable

Decodable : 자신을 외부표현(external representation)에서 디코딩 할 수 있는 프로토콜

### Encodable

Encodable : 자신을 외부표현(external representation)으로 인코딩 할 수 있는 프로토콜

__간단하게 보자면 Decodable과 Encodable은 서로 반대되는 기능을 가지고 있다고 생각하면 된다.__ 

---

### 프로토콜 채택

Codable은 `class`, `enum`, `struct`에서 모두 채택 가능하다.

Ex)

```swift
struct Person : Codable {
    var name : String
    var age : Int
}
```

그럼 이제 Codable을 채택한 Person은 어떻게 될까?

자신을 변환하거나 외부표현(external representation)으로 변환할 수 있는 타입. 이라고 명시되어 있다.

외부표현식으로 변환할 수 있다. 외부표현식 == JSON이라고 가정했을 때,

JSON으로 변환 할 수 있다는 것이다. == JSON으로 만들 수 있다.

