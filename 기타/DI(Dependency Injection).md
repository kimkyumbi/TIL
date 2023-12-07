# DI(Dependency Injection)

## Dependency(의존성)

DI는 Dependency Injection의 약자이다. 

의존성 주입을 설명하기 전에, 먼저 의존성부터 알아보는 것이 좋다.

객체지향 프로그래밍에서 의존성이란, 서로 다른 객체 사이의 의존 관계가 있다는 것을 의미한다.

이 경우, 의존하는 객체가 수정되면, 다른 객체도 영향을 받는다.

예를 들어서, 

```swift
struct GSM {
    func student() {
        print("학생")
    }

    func teacher() {
        print("선생님")
    }
}

struct Person {
    var person: GSM
    
    func student() {
        person.student()
    }
    
    func teacher() {
        person.teacher()
    }
}
```

위 코드에서 Person 객체는 GSM 객체를 사용하고 있으므로 GSM 객체에 대한 의존성이 생긴다.

이때, GSM에 수정사항이 생기거나 오류가 발생한다면 Person객체에도 영향을 줄 수 있다.

의존성을 가지는 코드가 많아진다면, 코드의 재활용성이 떨어지고, 매번 객체를 수정해야 한다는 단점이 있다.

그래서 나온 것이 의존성 주입, Dependency Injection이다.

## Injection(주입) 

주입은 외부에서 객체를 생성해 넣는 것을 말한다.

```swift
class GSM: Person {
    var student: String
    var teacher: String

    init(
        student: String, 
        teacher: String
    ) {
        self.student = student
        self.teacher = teacher
    }

    func printStudent() {
        print("학생")
    }

    func printTeacher() {
        print("선생님")
    }
}

let person = GSM(student: "학생", teacher: "선생님")
```

이렇게 생성자를 통해서 주입할 수도 있고, 다른 여러 가지 방법을 사용해서도 주입할 수 있다.

## Dependency Injection(의존성 주입)

#### 의존성 주입을 하면 좋아지는 점이 몇가지 있다.

- 코드 재사용성이 높아진다.
- Unit Test가 용이해진다.
- 객체 간의 의존성을 낮추거나, 없앨 수 있다.
- 객체 간의 결합도를 낮추어서 유연한 코드를 작성할 수 있다.

하지만 의존성 주입을 알기 전에, 의존성 관계 역전 법칠을 먼저 알아야 한다.

## Dependency Inversion Principle(의존성 관계 역전 법칙)

DIP, 의존 관계 역전 법칙은 객체 지향 프로그래밍 설계의 다섯가지 기본 원칙(SOLID) 중 하나이다. 

추상화가 된 것은 구체적인 것에 의존하면 안되고, 구체적인 것이 추상화되 것에 의존해야 한다는 것이다.

swift에서 추상화된 객체로는 protocol이 있다. 

```swift
protocol School {
    func printStudent()
    func printTeacher()
}
```

School 프로토콜은 printStudent와 printTeacher라는 함수를 가지고 있다. 

```swift
class GSM: School {
    var student: String
    var teacher: String

    init(
        student: String,
        teacher: String
    ) {
        self.student = student
        self.teacher = teacher
    }

    func printStudent() {
        print("학생")
    }

    func printTeacher() {
        print("선생님")
    }
}
```

그리고 GSM 클래스에서는 위에서 정의한 School 프로토콜을 채택하고 프로토콜에서 정의한 함수를 실체화해준다.

이제부터 중요하다.

```swift
struct Person {
    var todayLearn: School
    
    func printStudent() {
        todayLearn.printStudent()
    }
    
    func printTeacher() {
        todayLearn.printTeacher()
    }
    
    mutating func changeRole(school: School) {
        self.todayLearn = school
    }
}
```

위 코드에서, 기존의 방식과는 다르게 todayLearn 변수는 추상적인 객체 School에 의존하게 된다.

여기서 changeRole 함수를 통해서 의존성 주입을 할 수 있다.

이런 식으로 구현한다면 GSM객체와 Person객체는 거의 독립적인 객체가 된다. 

GSM 객체를 수정하거나 Person을 수정한다고 해서 상대 객체를 함께 수정해야 하는 문제를 방지할 수 있다. 