# 230926-1 / SWIFT / extension(확장) - 1

## 정의 

기존 클래스, 구조체, 열거형 타입에 새로운 Property, Method, Initializer 등을 추가하는 것으로,

원본 타입(소스 코드)에 접근하지 못하는 타입들도 확장해서 사용할 수 있다

extension이란 키워드를 사용하여 확장한다

문법은

```swift
extension AnyType: AnyProtocol, AniProtocol {

}
```

이렇게 extension 키워드 옆에 확장하고 싶은 타입을 쓴다.

프로토콜도 추가할 수 있다. 

## How To Use?

어떻게 쓰냐.. 

예를 들어 A라는 구조체가 있다. 

A구조체는 Hello World를 찍어주는 구조체다. 

우리는 이 A구조체를 찍을 때 맨 뒤에 !를 같이 출력하고 싶다. 

하지만 A구조체는 프레임워크에서 미리 정의된 구조체라서 건들 방법이 없다.

이때 extension을 사용하는 것이다. 

```swift
extension A {
    func print() {
        print("!")
    }
}
```

그럼 이제 print메서드를 사용할 수 있다.

하지만 여기서 주의할 점은,

우리가 A 원본을 건들지는 않았지만, 위처럼 확장할 경우

앞으로 A를 선언하는 모든 인스턴스는 A + extension 으로 구현된다.
