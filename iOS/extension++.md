# 230930-1 / SWIFT / extension(확장) - 3

## 확장에 생성자 추가 

### class에서의 생성자 추가

Designated initializer는 추가할 수 없고 

Convenience initializer만 추가할 수있으며,

deinitializer를 추가할 수 없다

?

그러니까 Deinitalizer는 extension으론 구현 불가, 

Designated도 불가하고,

오직 Convenience만 가능하다.

### struct에서 생성자 추가

extension으로 생성자를 추가할 경우,

Memberwise Initializer를 보존하며 새로운 생성자를 추가할 수 있다

간단하게 정리하자면, 구조체는 생성자를 만들지 않으면 스스로 기본 생성자를 만드는데,

이 기본 생성자는 구조체에서 생성자를 직접 만들 경우 제공되지 않는다.

하지만 extension을 통해서 이 기본 생성자를 보존하며 새로운 생성자를 추가할 수 있다.