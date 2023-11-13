# 230710-3 / SWIFT / enum case 나누기
```swift
import UIKit

// 학교 - 초, 중 고
enum School {
    // case elementary
    // case middle
    // case high
    case elementary, middle, high
    
}

var // 값을 변경할 수 있다

let // 값을 변경할 수 없다 - 상수

let yourSchool = School.high
print("yourSchool : \(yourSchool)")

enum Grade : Int {
    case first = 1
    case second = 2
}

let yourGrade = Grade.second
print("yourGrade : \(yourGrade.rawValue)")

enum SchoolDetail {
    case elmentary(name : String)
    case middle(name : String)
    case high(name : String)
    
    func getName() -> String { // gteName을 부르면 String을 반환한다
        switch self { // 자신이 가지는 값을 반환함
        case .elmentary(let name): // let name으로 들어온 것을 반환
            return name // 반환
        case let .middle(name): // 이렇게도 쓸 수 있음
            return name
        case .high(let name):
            return name
        }
    }
}

let yourMiddleSchoolName = SchoolDetail.middle(name: "중학교")

print("yourMiddleSchoolName : \(yourMiddleSchoolName)")
```
---
### ++ enum이 이해가 잘 안돼서 하는 추가 정리

`enum` 풀네임은 Enumeration (열거형)

- 열거형이란?
<br>
같은 주제로 연관된 데이터들을 멤버로 구성하여 나타내는 자료형이다.

즉, 공통된 주제에 대해서 이미 `정해놓은 입력 값` 만 선택해서 받고 싶을 때 사용하는 것이 열거형이다.

---

### 원시값이 없는 열거형

그냥 열거형 이름만 쓰고 선언해주면, 원시값이 없는 열거형이다.
```swift
// ex)
enum Position{
    case a
    case b
    case c
}
```
### 원시값이 있는 열거형

원시값이 없는 열거형에서 `case` 를 지정할 때 아무런 값도 넣지 않았지만, 원시값을 지정해줄 수도 있다.
<br>
이를 `Raw Value` 라고 하며, `Raw Value` 가 될 수 있는 자료형은 `Number, Character, String` 3가지가 있다.

---

### Number Type 

Int라는 타입을 enum 선언 시 이름 옆에 명시해주면,
가장 먼저 선언된 case부터 0부터 1씩 증가된 값이 들어간다.
```swift
// ex)
enum Position{
    case a // 0
    case b // 1
    case c // 2
}
```
- 만약 Raw Value를 직접 지정한다면  Raw Value가 없는 case는 이전 case + 1이 되어 값이 들어감

- Int형이 아닌 자료형으로 했을 경우에, 모든 case에 대해 값을 지정해주는 것이 아니면 에러가 발생함

- 따라서, Int형이 아닌 Number 자료형을 사용할 경우, Raw Value를 생략하고 싶다면, 
이전 case의 Raw Value를 정수 값으로 해주어야 한다. (정수 값으로 해도 형변환 되어 들어간다.)

---

### Character Type

- Character Type으로 열거형을 선언할 경우
모든 case에 대한 Raw Value를 직접 선언해주어야 한다.

---

### String Type

- String은 Character와 달리 Raw Value를 지정하지 않으면,
case 이름과 동일한 Raw Value가 자동으로 만들어진다.

---

### 원시 값이 있는 열거형의 경우는 Raw Value에 어떻게 접근할까?

이름 그대로 rawValue란 속성을 이용해 접근하면 된다.
 
만약, Raw Value가 있는 열거형의 경우,
Raw Value를 통해서도 열거형을 생성할 수 있는데, 이땐 다음과 같은 생성자를 이용하면 된다.
```swift
var A = Position(rawvalue: "a")
var B = Position(rawvalue: "b") 
```
근데, 만약 없는 Raw Value 값을 대입할 수 있으니,
이때 반환되는 열거형은 옵셔널 타입이다. (없는 Raw Value일 경우, nil 리턴)