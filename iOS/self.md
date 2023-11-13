# 230816-1 / SWIFT / self 프로퍼티

타입의 모든 인스턴스는 암시적으로 생성된 self 프로퍼티를 갖는다. 

이것은 인스턴스 자기 자신을 가리키는 프로퍼티이다.

self 프로퍼티는 인스턴스를 더 명확히 지칭하고 싶을 때 사용하게 된다. 

self 프로퍼티를 사용하여 자체 인스턴스 메서드 내에서 현재 인스턴스를 참조할 수 있다.

Swift에서의 프로퍼티 사용 순서는 자동으로 메서드 내부에 선언된 지역변수 ➜ 메서드 매개변수 ➜ 인스턴스 프로퍼티 순으로 찾아 무엇을 지칭하는지 유추한다.

```swift
class letterClass {
  var name: String = ""
  
  func sendLetter(to name: String) {
     print("\(name)에게 편지를 보냅니다.")
     self.name = name
  }
}
 
let Myletter: letterClass = letterClass()
Myletter.sendLetter(to: "GSM")
```

위 코드를 보면 인스턴스 프로퍼티인 name과 매개변수로 넘어온 name의 이름이 같은데,

여기서 self.name = name의 self는 매개변수가 아닌 인스턴스 프로퍼티를 지칭한다. 