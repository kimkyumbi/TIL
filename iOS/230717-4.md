# 230717-4 / SWIFT / inout
```swift
import UIKit

var title = ""

let jobTitle = "개발자"

//jobTitle = "김겸C"

func sayName(_ name: String) {
    print("안녕? 난 \(name) 라고 해")
}

func sayHi(_ name: inout String) { // 매개변수 자료형 앞에 inout을 넣으면 된다.
    name = "개발하는 " + name
    print("안녕? 난 \(name) 라고 해")
}

sayName("김겸B")

var name = "김겸D"

sayHi(&name) // inout은 앤드를 붙여야 한다. 변수 앞 앤드사인

// let과 같은 상수를 변경할 때 나는 에러가 inout을 하지 않았을 때도 발생한다
```
