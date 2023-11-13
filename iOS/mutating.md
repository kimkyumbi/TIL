# 230717-6 / SWIFT / mutating
```swift
import UIKit

class Friend { // class는 참조
    var name : String
    
    func changeName(newName: String){
        self.name = "김겸A " + self.name
    }
    init(_ name: String){
        self.name = name
    }
}

var myFriend = Friend("김겸B") // 원래 가지고 있던 이름이 김겸B

myFriend.changeName(newName: "개발하는 김겸B") // 개발하는 김겸B로 바뀜

myFriend.name


struct BestFriend { // struct는 값
    
    var name : String
    
    mutating func changeName(newName: String) { // struct안에서 멤버변수를 변경하고 싶다면 메서드 앞에 mutating을 붙인다.
        self.name = newName
        // print("newName: ", newName)
    }
//    init(_ name: String){
//        self.name = name
//    }
}

var myBestFriend = BestFriend(name: "김겸B")

myBestFriend.changeName(newName: "김겸C")

```

```swift
스트럭트의 경우
맴버 변수 name을 가지는 스트럭트
struct 는 참조(메모리 주소)인 클래스와 다르기 때문에
(클래스 vs 스트럭트 참조)
struct 구조의 맴버 변수 값을 변경(mutate) 하기 위해서는
mutating 키워드가 필요
``````