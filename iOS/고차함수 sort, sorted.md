# 230729-1 / SWIFT / 고차함수 sort, sorted (정렬)
```swift
import UIKit

var myArray = [3, 4, 88, 99, 5, 6, 7 , 8, 10, 20, 100]

var ascendingArray = myArray.sorted()

myArray.sort()

var descendingArray = myArray.sorted(by: >)

myArray.sort(by: >)
```