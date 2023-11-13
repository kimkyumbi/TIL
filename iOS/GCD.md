# 230918-1 / SWIFT / GCD

GCD : Grand Central Dispatch

DispatchQueue

Serial, Concurrent 

DispatchQueue에는 두 가지가 있다.

Serial Queue : 등록된 작업을 한번에 하나씩 차례대로 처리 하는 직렬의 Queue.

Concurrent Queue : 등록된 작업을 한번에 하나씩 처리 하지 않고 여러 작업들을 동시에 작업하는 병렬의 Queue.

기본은 Serial Queue이고, Concurrent Queue로 사용하려면 따로 attributes 선언을 해줘야 한다.

## Sync, Async

<a href = "https://github.com/kimkyumbi/TIL/blob/main/iOS/230914-1.md" > 동기(sync)와 비동기(async) </a> 

## Main, Global

앱 실행시 시스템에서 기본적으로 2개의 Queue를 만들어 주는데, 그것이 Main Queue와 Global Queue 이다.

### Main Queue

메인 스레드에서 사용 되는 Serial Queue. 모든 UI 처리는 메인 스레드에서 처리를 해야한다.

### Global Queue

편의상 사용할 수 있게 만들어 놓은 Concurrent Queue. 

처리 우선 순위를 위한 QOS(Quality of Service) 파라미터를 제공한다. 

작업 완료의 순서는 정할 수 없지만 우선적으로 일을 처리하게 할 수 있다!

### Custom Queue

GlobalQueue에서 수행되는 임의로 정의한 Queue.

Serial & Concurrent 모두 가능하나 보통 Serial 작업 수행. Main과 구분해 사용이 필요할 때 사용

### Conclusion

sync는 작업이 끝날 때까지 기다리기 때문에 UI 업데이트는 main thread의 async만 사용 가능하다.

raywenderlich 예제에서는 UI 업데이트를 위해 아래와 같이 코드를 작성하고 있다.

```swift
DispatchQueue.global(qos: .userInteractive).async {
  forLoop("선행 작업")
  
  DispatchQueue.main.async {
    print("선행 작업 후 UI 변경")
  }
}
``````

이렇게 하면 서버에서 데이터를 받아오거나, 사전에 처리해야할 부분이 있을 경우 UI업데이트를 자연스럽게 할 수 있다고 한다!