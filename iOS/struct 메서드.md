# 230718-1 / SWIFT / struct 메서드
```swift
import UIKit

struct Freind {
    
    var age : Int
    
    var name : String
    
    func sayHello() -> String {
        print("안녕")
        return "저는 \(age)살, \(name)입니다."
    }
}

var myFriend = Freind(age: 10, name: "김겸B")

myFriend.sayHello()
```
struct도 메서드가 가능하다...!!
