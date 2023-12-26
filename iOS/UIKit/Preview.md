# UIKit - SwiftUI의 프리뷰 띄우기

```swift
import SwiftUI

struct ViewControllerRepresentable: UIViewControllerRepresentable {
    typealias UIViewControllerType = ViewController
    
    func makeUIViewController(context: Context) -> ViewController {
        return ViewController()
    }
    
    func updateUIViewController(_ uiViewController: ViewController, context: Context) {
    }
}

@available(iOS 13.0.0, *)
struct ViewPreview: PreviewProvider {
    static var previews: some View {
        ViewControllerRepresentable()
    }
}
```

Swiftui를 import해주고,

위 코드를 쓰면 된다. 

저 코드는 SwiftUI를 UIKit에서 쓸 수 있게 해 주는 코드이다.