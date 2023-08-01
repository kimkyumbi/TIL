# 230801-1 / SWIFT / Getter, Setter
```swift
import UIKit

class Friend {
    
    var name: String
    var age: Int
    
    var detailInfo : String = ""
    
    var info : String { // 값을 설정해 여러 데이터들을 조합해 get
        get{
            return "내 친구: \(name) / 나이: \(age)"
        }
        set {
            detailInfo = "info 에서 설정됨 :" + newValue
        }
    }
    
    init(_ name: String, _ age: Int){
        self.name = name
        self.age = age
    }
    
}

let myFriend = Friend("김겸비", 16)

myFriend.info = "김겸B"
myFriend.detailInfo
```
