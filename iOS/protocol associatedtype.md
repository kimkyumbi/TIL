# 230721-1 / SWIFT / protocol associatedtype 
```swift
import UIKit

protocol PetHaving {
    associatedtype T
    var pets: [T] { get set }
    mutating func gotNewPet(_ newPet: T)
}

extension PetHaving {
    mutating func gotNewPet(_ newPet: T) {
        self.pets.append(newPet)
    }
}

enum Animal {
    case cat, dog, bird
}

struct Friend : PetHaving {
    var pets: [Animal] = []
}

struct Family : PetHaving {
    var pets: [String] = []
}

var myFriend = Friend()

myFriend.gotNewPet(Animal.bird)
myFriend.gotNewPet(Animal.cat)
myFriend.gotNewPet(Animal.dog)
myFriend.pets

var myFamily = Family()
myFamily.gotNewPet("거북이")
myFamily.gotNewPet("토끼")
myFamily.gotNewPet("강아지")
myFamily.pets

```
프로토콜에서 제네릭 타입을 사용할 땐 `associatedtype` 을 사용하면 된다.
