# 230808-1 / SWIFT / Color

- 색깔을 가진 뷰

```swift
Color(.blue)
```
이때 safearea를 빼고 전부 색을 채워준다.

- safearea는 폰 위쪽 양 부분과 아래쪽 바를 가리킨다.

하지만 

```swift
Color(.blue).edgesIgnoringSafeArea(.All)
```

`.edgesIgnoringSafeArea(.All)` 이렇게 써주면 

safearea를 무시하고 전부 색을 채운다. 

이 외에도 다양한 기능이 있다

```swift
Color(red: , green: , blue: )
```

이렇게 RGB값을 숫자를 넣어 조정해 다양한 색을 만들 수도 있다.

