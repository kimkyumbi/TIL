# 230927-1 / SWIFT / extension(확장) - 2

## 프로퍼티 추가하기 

* 연산 프로퍼티만 추가 가능

```swift
extension Int {
    var half: Int {
        return self / 2
    }
}
```

이렇게 선언한 프로퍼티는 

```swift
let num = 100
print(num.half) // 50
```

이렇게 모든 Int에서 사용이 가능하다. 

## 메서드 추가하기 

인스턴스, 타입 메서드를 추가할 수 있다. 

```swift
// 타입 메서드
extension Int {
    static func printZero() {
        print(0)
    }
}
 
Int.printZero() // 0
 
// 인스턴스 메서드
extension Int {
    func printDouble() {
        print(self * 2)
    }
}
 
let num = 100
num.printDouble() //200
```
