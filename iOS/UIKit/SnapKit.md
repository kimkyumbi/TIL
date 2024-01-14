# UIKit - SnapKit 

스냅킷은 autolayout을 더 쉽게 사용할 수 있게 해주는 프레임워크이다.

## 중요한 것 

해석 순서가 매우 중요하다. SnapKit을 쓸 때 

```swift
make.top.equalTo(viewSnapKit.snp.bottom).offset(32)
```

이렇게 작성하게 되는데 이때 해석 순서는 

    make(만든다) -> top(상단을) -> equalTo(viewSnapKit.snp.bottom)(viewSnapKit의 하단과 동일하게) -> offset(32)(offset은 32로 지정)

이렇데 된다.

## Anchor 

모든 앵커와 제약 조건 자체를 함께 연결하는것이 가능하다.

```swift
gsm.snp.makeConstraints { make in
  make.lead.top.trailing.bottom.snapkitview()
}

// edge를 이용하면 한번에 쓸 수 있다.
gsm.snp.makeConstraints { make in
  make.edges.snapkitview()
}
// inset() 을 줄수도 있다.
gsm.snp.makeConstraints { make in
  make.edges.snapkitview().inset(16)
}
```

## Constraint

### multipliedBy()

```swift
// superview의 너비와 같게 만들고 0.45를 곱한 형태
make.width.snapkitview().multipliedBy(0.45)
```

### offset()

```swift
// 상단을 viewSnapKit의 하단으로 제한하고, 32만큼 offset
make.top.equalTo(viewSnapKit.snp.bottom).offset(32)
```

offset: element와의 간격에 사용

inset: superview와의 간격에 사용
