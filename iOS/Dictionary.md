# 230717-1 / SWIFT / Dictionary
```swift
import UIKit

var myFriends = ["bestFriend" : "김겸A",
                 "highschool" : "김겸B"
                ]

let myBestFriend = myFriends["bestFriend"]

let highSchoolFriend = myFriends["highschool"]

// let youtubeFriend = myFriends["youtube"] 데이터가 없으니 nil값

let youtubeFriend = myFriends["youtube" , default: "친구 없음"] //. 친구 없음 값

myFriends["bestFriend"] = "개발하는 김겸C"

let myBF = myFriends["bestFriend"]

myFriends["newFriend"] = "김겸D"

let newFriend = myFriends["newFriend"]

myFriends.updateValue("김겸E", forKey: "김겸F")

let girlFriend = myFriends["girlFriend"]

myFriends.updateValue("김겸G", forKey: "김겸H")

let myBestFriend2 = myFriends["bestFriend"]

// let emptyDictionary : [String : Int] = [:]
let emptyDictionary = [String : Int]()

let myEmptyDictionary : [String : Int] = Dictionary<String, Int>()

myFriends.count

for item in myFriends {
    print("item : ", item)
}
```