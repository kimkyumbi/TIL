# Tuple 

## 튜플? 

tuple은 여러 가지의 타입들은 한번에 묶어서 사용할 수 있게 해 준다. 

```swift
var tuple = (1, "안녕하세요")

var tuple2 = (2, (tuple))
```

tuple 변수는 Int값인 1과 String값인 안녕하세요를 둘 다 담고 있다. 

또한 tuple안에 tuple을 넣을 수도 있다. 

tuple2변수가 그 예이다. 

호출도 가능하다. 

`tuple.` 이렇게 tuple 앞에 점을 찍으면 인덱스처럼 0, 1 로 나오게 된다. 

이것으로 접근할 수 있다. 

tuple안에 있는 tuple에 접근하려면 

`tuple.1.2` 이런식으로 접근할 수 있다.

---
### 튜플 안에 이름 넣기 

또 tuple에는 이름도 줄 수 있는데, 

```swift
var tuple = (1, "안녕하세요")

var tuple2 = (2, (tuple))

위의 코드에서 

var tuple = (number: 1, name: "안녕하세요")

var tuple2 = (number: 2, name: (tuple))

이렇게!
```

이렇게 이름을 줘서 이름으로 호출을 하거나 접근할 수 있다. 

또한, 이름과 타입만 주고 따로 값을 넣어줘도 된다!

--- 
### 튜플 안에 배열 넣기

튜플 안에는 배열도 넣울 수 있다. 

하지만 튜플은 Sequence라는 프로토콜을 준수하고 있지 않기 때문에, 루프를 돌릴 수 없다.

루프를 돌리려면 배열 안에 튜플을 넣으면 된다. 

이때 주의할 점은, 배열 안에 튜플을 넣을 때에는 튜플 안에 들어가는 타입과 순서가 모두 같아야 한다는 것이다. 

처음에 Int를 넣어주면 다른 모든 튶플에도 처음엔 Int가 들어가야한다.

---

### var (a, b) = tuple 

이런식으로 쓰더라도 괄호 안에 해당 튜플의 개수와 맞게 선언해주면 사용이 가능하다!

---

### 여러 가지의 타입을 한번에 리턴할 수 있다

일반적으로 함수를 만들 때, 리턴 타입은 한개이다. 

하지만 튜플을 리턴할 수 있다.

```swift
func tuple() -> (Int,String,Bool) {   
    return (1, "안녕하세요", true)
}
```

이렇게 말이다.

---

### typealias 

와 같이 쓸 수 있다.

```swift
typealias People = (name:String, age:Int, likes:[String])
```

People이라는 타입을 튜플로 만들고,

변수에 People 타입을 지정해주면?

```swift
var people1: People = ("KGB", 18, ["heart", "iOS"])
```

이렇게 튜플을 받을 수 있다.

```swift
var peopleArr : [People] = [("Zedd",999,["Swift","iOS"]),("Your_Name",123,["Piano","Poet"])]
```

배열로도 받을 수 있다.