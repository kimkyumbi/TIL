# UIKit - UIImageView

UIImageView는 이미지를 넣을 수 있는 view이다.

```swift
let imageView: UIImageView = {
        let imageView = UIImageView()
        imageView.backgroundColor = .red
        //표시될 UIImage 객체 부여
        imageView.image = UIImage(named: "ImageName")
        imageView.translatesAutoresizingMaskIntoConstraints = false
        return imageView
    }()
```
