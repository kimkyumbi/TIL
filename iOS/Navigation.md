# 231019-1 / SWIFT / Navigation

swiftui 에는 NavigationView, NavigationStack, NavigationLink 가 있다.

## NavigationVIew

NavigationView를 stack으로 사용하기 위해서는 navigationViewStyle 수정자에서 stack을 선택했어야 했다.

NavigationView는 더이상 사용하지 않는다.

## NavigationStack

네비게이션 즉 뷰, 화면 전환의 네비게이션 방식이 있다.

완전히 흐름이 다른 뷰로 넘어가게 되는 방식이다.

이 방식을 스택처럼 적용했다는 것이다.

NavigationStack은 NavigationView와 비슷하지만, 이젠 navigationViewStyle 수정자로 stack을
선택할 필요가 없다.

## NavigationLink

내가 눌렀을 때 원하는 View 가 나오는 역할을 하게 된다.

하지만 NavigationLink 만 있다고 해서 다음 View로 넘어가지는 않고 새로 만들어진 

.navigationDestination(for: ) 수정자를 사용해야 한다.

### navigationDestination

.navigationDestination(for: ) 는 특정 종류의 데이터를 제공할 때 

Stack이 가리키는 View 를 보여주게 됩니다.

즉, View 를 데이터 유형과 연결하게 되고 동일한 종류의 데이터 인스턴스를 제공하는 NavigationLink 를 초기화 하게됩니다.

