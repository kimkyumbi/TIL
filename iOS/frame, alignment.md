# 230810-1 / SWIFT / frame & alignment
# frames & alignments

## frame 

- 화면의 여러 뷰들을 감싸는 사각형의 영역

`frame`은 영역을 지정해주지 않았을 때 기본적으로 차지하는 영역이 있다. 

이때 `frame`의 영역을 지정해주면 지정한 만큼의 영역을 차지한다. 

예를 들어, 
```swift
Text("Hello, MSG!")
	.background(Color.blue) // Text 자체의 영역
```
이렇게 따로 `frame`을 지정해주지 않는다면 기본적으로 가지는 영역만을 차지하게 된다.

하지만 
```swift
Text("Hello, MSG!")
    .background(Color.blue) // Text 자체의 영역 
    .frame(width: 20, height: 20) // Text의 frame영역
```
이렇게 `frame`을 이용해 영역을 지정해준다면 지정된 영역만큼 차지하게 되는 것이다. 

이런 방식은 고정적으로 frame을 지정하는 것인데, 이미지와 텍스트의 내용에 따라 사이즈가 유동적으로 바뀌어야 할 때는 

```swift
minWidth: 10, // 최소 너비 지정
idealWidth: 300, // 최적 너비 지정
maxWidth: .infinity, // 최대 너비 지정
minHeight: 10, // 최소 높이 지정
idealHeight: 300, // 최적 높이 지정
maxHeight: .infinity, // 최대 높이 지정
```

이렇게 지정해줄 수도 있다. 

## alignment

- 정렬

frame을 설정할 때 세번째 인자로 alignment를 볼 수 있다. 

말 그대로 정렬이기 때문에, 다양한 방식으로 정렬을 해줄 수 있다.

left 대신 leading, right 대신 trailing을 쓴다.
