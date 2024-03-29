# 231006-1 / SWIFT / @Published

@Published 와 @Observedobject 를 알아보기 전에 

ObservableObject를 알고 가면 좋다. 

간단하게 정리하면 이 프로토콜을 따르는 클래스 인스턴스를 관찰하다 어떠한 값이 변경되면 뷰 업데이트를 해준다.

## @Published

@Published는 프로퍼티 래퍼이다.

@Published를 붙여 만들면 이 유형으로 생성된다.

```swift
class Weather {
    @Published var temperature: Double
    init(temperature: Double) {
        self.temperature = temperature
    }
}

let weather = Weather(temperature: 20)
cancellable = weather.$temperature
    .sink() {
        print ("Temperature now: \($0)")
}
weather.temperature = 25

// Prints:
// Temperature now: 20.0
// Temperature now: 25.0
```

간단한 예제를 보자. 

위 예제에서 Weather 클래스를 만들어 temperature 프로퍼티에 @Published를 붙여 생성한다. 

그리고 weather 인스턴스를 만든다.

값 변화를 파악하기 위해 설정해주고 해당 $temperature를 이용해 게시자에 엑세스 할 수 있도록 해준다.

그러고 해당 값을 변화시켜주면 출력문이 해당 값에 맞게 출력되게 된다.

그런데 여기서 새로운 값이 실제로 설정되기전에 sink블럭이 실행됨으로 두번 현재값과 변경값이 출력되게 된다.

또한 해당 속성은 오직 클래스에서만 쓸 수 있다.

즉 뷰와 연결하면 해당 값이 변화할때 마다 업데이트를 하는 것이다.
