# 230730-1 / SWIFT / private(set)
```swift
import UIKit

struct MyPet {
    
    var title :String = "타이틀없음"
    
    private (set) var name :String = "이름없음"
    
    mutating func setName(to newName: String){
        self.name = newName
    }
}

var myPet = MyPet()
//myPet.name
//myPet.title
//myPet.title = "김겸B"
//myPet.title
//myPet.name = "김겸비"
myPet.setName(to: "김겸비")
myPet.name
```