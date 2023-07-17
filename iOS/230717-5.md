# 230717-5 / SWIFT / Error
```swift
import UIKit

enum MismatchError: Error { // 에러를 이넘 타입으로 만들 수 있다.
    case nameMismatch
    case numberMismatch
}

// 에러를 던지는 메소드
func guessMyName(name input: String) throws {
    print("guessMyName() called")
    
    if input != "김겸A" {
        print("x")
        throw MismatchError.nameMismatch
        // return
    }
    print("o")
}


/// 번호를 맞춘다
/// - Parameter input: 사용자 숫자 입력
/// - Returns: bool 맞췄는지 여부
func guessMyNumber(number input: Int) throws -> Bool {
    print("guessMyName() called")
    
    if input != 10 {
        print("x")
        // throw MismatchError.nameMismatch
        // return
    }
    print("o")
    return true
}

try? guessMyName(name: "김겸B") // 에러를 받지 않겠다.

try! guessMyName(name: "김겸B") // 에러가 무조건 없다.

do {
   try guessMyName(name: "김겸B")
} catch {
    print("잡은 에러: \(error)")
}

do {
    let receivedValue = try guessMyNumber(number: 9)
} catch {
    print("잡은 에러: \(error)")
}
```