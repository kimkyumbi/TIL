# iOS - ARC 

ARC(Automatic Reference Counting)는 자동으로 메모리를 관리해주는 기능이다. 

ARC는 참조 카운트를 관리하고, 참조 카운트가 0이 되면 메모리를 해제한다.

```swift
class MSG {
    let gsm: String
    init(name: String) {
        self.name = name
        print("\(name) is MSG")
    }
    deinit {
        print("\(name) is GSM")
    }
}
var reference1: MSG?
var reference2: MSG?
var reference3: MSG?

reference1 = MSG(name: "GSM")
reference2 = reference1
reference3 = reference1
```

위 코드에서 MSG 객체의 참조 카운트는 3이 된다. 

만약 여기서,

```swift
reference1 = nil
reference3 = nil
reference2 = nil 
```

이 코드가 이어서 있다면, 

MSG 객체의 참조를 차례대로 해제함으로써 참조 카운트는 0이 된다. 

## Strong Reference Cycle

하지만, 두개의 클래스 객체가 서로를 강하게 참조하고 있다면 어떻게 될까? 

이러한 경우를 Strong Reference Cycle이라고 한다. 

Strong Reference Cycle은 

```swift
class GSM {
    var msg: MSG?

    deinit {
        print("deinit GSM")
    }
}

class MSG {
    var gsm: GSM?

    deinit {
        print("deinit MSG")
    }

}

var a: GSM? = GSM()
var b: MSG? = MSG()

a?.msg = b
b?.gsm = a
```

위 코드처럼 GSM 클래스와 MSG클래스가 서로를 참조하고 있을 때, 

GSM과 MSG를 각각 참조하고 있는 a와 b의 메모리를 해제하더라도,

서로가 서로를 참조하고 있다면 Reference Count가 0이 되지 않고 1인 상태로 계속 남아있게 된다.

이렇게 된다면 메모리 누수가 발생할 수도 있다.

물론 해결할 방법이 있다. 

---

## weak, unowned

weak과 unowned는 둘 다 reference count를 증가시키지 않는다.

그러므로 weak와 unowned는 Strong Reference Cycle을 방지하고, 해결할 수 있다. 

### weak

weak Reference는 객체에 강한 참조를 유지하지 않기 때문에, ARC가 참조하는 객체를 해제하려고 할때 막을수가 없다. 

이로인해 strong reference cycle을 피할수 있게 된다.

만약 weak는 자신이 가리키고 있는 instance가 메모리로부터 해제되면 ARC에서 자동적으로 nil을 처리한다.

이전 코드에서, msg와 gsm 변수 앞에 weak를 붙이면 서로 참조를 하더라도 참조 카운트를 증가시키지 않기 때문에 Strong Reference Cycle이 발생하지 않게 된다. 

하지만 변수를 weak로 선언한다면, 런타임 때 자동적으로 nil로 변하는 것을 허락해야 하기 때문에 옵셔널로 선언해야 한다. 

```swift
class GSM {
    weak var msg: MSG?

    deinit {
        print("deinit GSM")
    }
}

class MSG {
    weak var gsm: GSM?

    deinit {
        print("deinit MSG")
    }

}

var a: GSM? = GSM()
var b: MSG? = MSG()

a?.msg = b
b?.gsm = a

a = nil
b = nil
```

위 코드처럼 변수 앞에 둘 다 weak를 붙여도 되지만, 

둘중 하나에만 weak를 붙여도 결과는 변하지 않는다.

### unowned 

unowned는 weak와 달리 항상 갑이 있다는 전제하에 사용된다. 

그래서 옵셔널을 만들지 않고, ARC 또한 자동적으로 unowned reference를 nil로 처리하지 않는다. 

그리하여 unowned는 weak와 달리 system을 abort시킬수 있는 위험이 있기 때문에 주의해서 사용해야 한다.

```swift
class GSM {
    unowned var msg: MSG?

    deinit {
        print("deinit GSM")
    }
}

class MSG {
    unowned var gsm: GSM?

    deinit {
        print("deinit MSG")
    }

}

var a: GSM? = GSM()
var b: MSG? = MSG()

a?.msg = b
b?.gsm = a

a = nil
b = nil
```

weak의 코드에서 weak를 unowned로 바꾸어도 결과는 변하지 않는다.