# 230902-1 / SWIFT / class

swift에서는 객체라는 용어 대신에 인스턴스 라는 용어를 사용한다. 

한마디로 클래스 타입의 인스턴스를 객체라고 칭하지 않는다. 

클래스와 인스턴스는 간단하게 생각하면 붕어빵 기계와 기계로 만들어진 붕어빵이라고 할 수 있다.

붕어빵을 만드는 기계(틀)이 클래스이고 그 틀로 만들어진 붕어빵이 인스턴스가 되는 것이다. 

---

## 클래스의 구조 

swift의 기본적인 클래스 구조는 아래처럼 되어 있다.

```swift
class ClassName : superClass {
	var vName1 = 1
	var vName2 = 4
    
	func fName1() -> Any {
	}
    
	func fName2() -> Any {
	}	
}
```

즉, 클래스 파일을 메모리에 올리면 객체화가 되고,

인스턴스들의 속성과 명령어가 실행되면서 프로그램이 실행되는 것이다.

---

## 클래스 인스턴스의 생성과 초기화 

클래스를 정의하고 초기화를 할 때에는 따로 초깃값을 정해주지 않고 이니셜라이저를 이용하면 된다. 

인스턴스가 생성되고 이니셜라이즈 된 후에 구조체와 마찬가지로 마침표를 쓰면 되는데, 여기서 차이점은

struct는 변수만 변경할 수 있지만 class 는 변수나 상수 상관 없이 변경할 수 있다는 것이다. 

클래스는 참조타입 이고 구조체는 값 타입이다.

## 프로퍼티 및 메서드

### 프로퍼티 및 메서드 구현

```swift
class Sample {
    // 가변 프로퍼티
    var mutableProperty: Int = 100 

    // 불변 프로퍼티
    let immutableProperty: Int = 100 
    
    // 타입 프로퍼티
    static var typeProperty: Int = 100 
    
    // 인스턴스 메서드
    func instanceMethod() {
        print("instance method")
    }
    

    // 타입 메서드
    // 상속시 재정의 불가 타입 메서드 - static
    static func typeMethod() {
        print("type method - static")
    }
    
    // 상속시 재정의 가능 타입 메서드 - class
    class func classMethod() {
        print("type method - class")
    }
}
```
