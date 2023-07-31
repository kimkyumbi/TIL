# 230731-1 / SWIFT / foreach문에서 인덱스 가져오기
```swift
let myFriendsArray = ["a", "b", "c", "d"]

// foreach 반복문에서 enumerated를 통해 해당하는 인덱스를 가져올 수 있다.
for (friendIndex, friendItem) in myFriendsArray.enumerated() {
    print("\(friendIndex): \(friendItem))
}
```