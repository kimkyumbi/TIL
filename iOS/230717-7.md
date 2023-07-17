# 230717-7 / SWIFT / Set
```swift
import UIKit

// 배열과 비슷한 set
// 배열처럼 중복으로 값을 넣을 수 없다.
// 아무리 넣어도 고유한 녀석들만 남는다.
var myNumberSet : Set<Int> = Set<Int>()

myNumberSet.insert(1)
myNumberSet.insert(2)
myNumberSet.insert(2)
myNumberSet.insert(3)
myNumberSet.insert(3)

myNumberSet.count // myNumberSet의 순서는 가져올 때마다 달라진다.
myNumberSet

// 배열과 다르게 순서가 정해져있지 않다.
// 매번 출력되는 값들의 순서가 다르다
for aNumber in myNumberSet {
    print("aNumber: ", aNumber)
}

var myBestFriends : Set<String> = ["겸A", "겸B", "겸C"]
myBestFriends.contains("겸C")

var myFriends : Set<String> = ["겸A", "겸B", "겸C"]
myFriends.contains("겸D")

// 그 외에도 콜렉션 [배열, 셋, 딕셔너리, 튜플] 등이 가지고 있는 기본 메서드 들을 제공한다.
myFriends.contains("김겸비")

// 겸C의 Set 인덱스를 가져온다.
if let indexToRemove = myFriends.firstIndex(of: "겸C") {
    // 겸C를 지운다.
    print("indexToRemove: ", indexToRemove)
    myFriends.remove(at: indexToRemove)
}

if !myFriends.contains("겸C") {
    print("내 친구중에 겸C가 없다....")
}
```