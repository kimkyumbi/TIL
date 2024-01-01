# UIKit - UIButton 

말이 필요없다. 코드를 보도록 하자.

```swift
import UIKit

class ViewController: UIViewController {
    
    lazy var button: UIButton = {
        let button = UIButton()
        button.setTitle("버튼입니다", for: .normal)
        button.backgroundColor = .lightGray
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        view.addSubview(button)
        button.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 20).isActive = true
        button.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -20).isActive = true
        button.topAnchor.constraint(equalTo: view.topAnchor, constant: 300).isActive = true
    }
}
```

버튼의 setTitle 속성을 이용해 버튼에 들어갈 텍스트와 for을 통해 버튼의 상태를 정할 수 있다.
