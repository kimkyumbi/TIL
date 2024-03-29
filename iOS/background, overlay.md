# 230811-1 / SWIFT / background & overlay
# Backgrounds & Overlays

## Background

우리는 background를 보통 뒷배경의 색을 바꿀 때 사용했지만 실제로는 뷰의 하위계층을 쌓아가는 것이다. 

```swift
Rectangle().fill(Color.blue).frame(width: 150, height: 150)
    .background(Rectangle().fill(Color.yellow)) 
```
위 코드를 보면 파란색 사각형을 만들고 background에 노란색 사각형을 만들었다.

이때 실행화면을 보면

![Alt text](<../사진/스크린샷 2023-08-07 오후 4.19.22.png>)

이렇게 하위계층을 쌓았기 때문에 파란색 사각형이 보인다.

## Overlay

```swift
Rectangle().fill(Color.blue).frame(width: 150, height: 150)
    .overlay(Rectangle().fill(Color.yellow)) // 뷰 중첩 오버레이, 크기 안정하면 동일해서 겹침

```
똑같이 파란색 사각형을 만들었지만 background대신 overlay를 넣었다.

이때 실행화면은

![Alt text](<../사진/스크린샷 2023-08-07 오후 4.20.01.png>)

이렇게 overlay는 위로 쌓는것이기 때문에 노란색 사각형이 보인다.

이렇게 background와 overlay의 차이점은 앞에 쌓느냐, 뒤에 쌓느냐의 차이인다. 
