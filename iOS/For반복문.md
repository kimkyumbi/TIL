# 230710-4 / SWIFT / For 반복문
```swift
import UIKit

// 레인지
// 0...5 > 0에서부터 5까지
// 0,1,2,3,4,5

//0..<5 0에서부터 5보다 작을 때까지
// 0,1,2,3,4

// 0부터 5까지
for index in 0...5 {
    print("호호 index : \(index)")
}

// 0부터 4까지 짝수인 수만
for index in 0..<5 where index % 2 == 0 {
    print("호호 짝수 index : \(index)")
}

// var randomInts ; [Int] = []
var randomInts : [Int] = [Int]() // 랜덤


// 변수라고 생각하면 됨
// i 는 사용하지 않으면 _ 언더바로 쓰면 됨
for _ in 0..<25 {
    let randomNumber = Int.random(in: 0...100)
    randomInts.append(randomNumber)
}

print("randomInts : \(randomInts)")

```