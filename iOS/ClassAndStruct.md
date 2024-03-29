# 230712-1 / SWIFT / Class와 Struct
```swift
import UIKit

// 유튜버 (데이터) 모델 - struct / 구조체
struct YoutuberStruct {
    var name : String
    var subscribersCount : Int
}

var devJeong = YoutuberStruct(name : "김겸비", subscribersCount:  99999)

var devJeongClone = devJeong // 값 복사

print("devJeongClone.name : \(devJeongClone.name)")

devJeongClone.name = "김겸B"

// 값 복사이기 때문에 둘의 값이 다르다
print("devJeongClone.name : \(devJeongClone.name)")

print("devJeongClone.name : \(devJeong.name)")

// 클래스
class YoutuberClass {
    var name : String
    var subscribersCount : Int
    // 생성자 - 즉 메모리에 올린다
    // init 으로 매개변수를 가진 생성자 메소드를 만들어야
    // 매개변수를 넣어서 그값을 가진 객체(object)를 만들 수 있다.
    init(name: String, subscribersCount: Int){
        self.name = name
        self.subscribersCount = subscribersCount
    }
}

var jeongDaeRi = YoutuberClass(name : "김겸비", subscribersCount: 99999)

var jeongDaeRiClone = jeongDaeRi // 값 공유

print("jeongDaeRiClone.name : \(jeongDaeRiClone.name)")

jeongDaeRiClone.name = "김겸B" // jeongDaeRi 도 값이 김겸B로 바뀜

print("jeongDaeRiClone.name : \(jeongDaeRiClone.name)") // 출력결과 : 김겸B

print("jeongDaeRi.name : \(jeongDaeRi.name)") // 출력결과 : 김겸B
```
`struct`는 값을 복사해 각각의 변수에 값이 저장되어 값이 다르지만, `class`는 연결되어있기 때문에 값이 같이 변해 똑같다.