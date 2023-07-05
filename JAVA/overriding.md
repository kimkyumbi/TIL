# Overriding
---
오버라이딩(overriding)이란 상속 관계에 있는 부모 클래스에서 이미 정의된 메소드를 자식 클래스에서 같은 시그니쳐를 갖는 메소드로 다시 정의하는 것이라고 할 수 있습니다.

### 오버라이딩의 조건
자바에서 메소드를 오버라이딩하기 위한 조건은 다음과 같습니다.

- 오버라이딩이란 메소드의 동작만을 재정의하는 것이므로, 메소드의 선언부는 기존 메소드와 완전히 같아야 합니다.

        하지만 메소드의 반환 타입은 부모 클래스의 반환 타입으로 타입 변환할 수 있는 타입이라면 변경할 수 있습니다.

- 부모 클래스의 메소드보다 접근 제어자를 더 좁은 범위로 변경할 수 없습니다

- 부모 클래스의 메소드보다 더 큰 범위의 예외를 선언할 수 없습니다.

**자바에서는 메소드 오버라이딩을 통해 상속받은 부모 클래스의 메소드를 자식 클래스에서 직접 재정의할 수 있습니다.**

아래 코드는 부모 클래스인 Parent 클래스의 display() 메소드를 자식 클래스인 Child 클래스에서 오버라이딩하는 코드입니다.

```java
class Parent {
    void display() { System.out.println("부모 클래스의 display() 메소드입니다."); }
}

class Child extends Parent {
    void display() { System.out.println("자식 클래스의 display() 메소드입니다."); }
}

public class Inheritance05 {
    public static void main(String[] args) {

        Parent pa = new Parent();

        pa.display();

        Child ch = new Child();

        ch.display();

        Parent pc = new Child();

        pc.display(); // Child cp = new Parent();
    }
}
// 실행결과
// 부모 클래스의 display() 메소드입니다.
// 자식 클래스의 display() 메소드입니다.
// 자식 클래스의 display() 메소드입니다.
```
