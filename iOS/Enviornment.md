# 230903-1 / SWIFT / @Enviornment

## @Environment

- @Environment 를 통해서 알 수 있는 정보는 디바이스가 다크모드인지 라이트모드인지 뷰가 렌더링되는 크기 클래스 등 시스템에서 제공하는 고정되어있는 속성에 접근이 가능

- 자식뷰에서 @Environment를 선언하여, 뷰모뷰에서 주입해주는 EnvionmentValues 값을 사용

- 특정 프로퍼티의 값이 변경되면 뷰에도 업데이트되는 기능이 존재

- key값은 EnvironmentValues 형태이며, EnvironemntValues 값은 커스텀해서 만들 수 있고 SwiftUI에서 미리 정해진 값들이 존재