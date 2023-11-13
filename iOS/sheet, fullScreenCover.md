# 231019-2 / SWIFT / sheet, fullScreenCover

Sheet와 FullScreenCover

ZStack과 Overlay처럼 뷰를 중첩하기 위한 방법으로 .sheet, .fullScreenCover를 이용할 수 있다.

sheet는 화면을 모두 채우지 않고 조금 남는 반면에 fullScreenCover은 이름처럼 화면을 전부 채운다.

그래서 sheet는 스크롤을 통해 이전 뷰로 돌아갈 수 있지만, 

fullScreenCover는 이전 뷰로 돌아갈 수 없다.

그냥 바인딩만 이용해주면 된다.

```swift
struct SwiftUIStudy: View {
    
    @State var isThisSheet: Bool = false
    @State var isThisFullScreenCover: Bool = false
    
    var body: some View {
        VStack {
            Button {
                self.isThisSheet.toggle()
            } label: {
                Text("시트")
            }
            .sheet(isPresented: $isThisSheet) {
                Text("돌아가세요")
            }
            .padding()
            
            Button {
                self.isThisFullScreenCover.toggle()
            } label: {
                Text("풀 스크린 커버")
            }
            .fullScreenCover(isPresented: $isThisFullScreenCover) {
                Text("어딜가시죠")
            }
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333440077832295/1164460338700361728/2023-10-19_4.09.12.png?ex=65434b33&is=6530d633&hm=b8b56a99730ec2615e975adb01952ed798a16599a95d5926e5376533103e4dab&)

![image](https://cdn.discordapp.com/attachments/1147333440077832295/1164460338406756392/2023-10-19_4.09.19.png?ex=65434b33&is=6530d633&hm=a66f82ba30a355d932869060ad25f175f387338e71f714cde7e9b92712a4e4b6&)

![image](https://cdn.discordapp.com/attachments/1147333440077832295/1164460338134142986/2023-10-19_4.09.27.png?ex=65434b33&is=6530d633&hm=8e153036875f87433474b432a4b02fb6e0806fc55144e90b88b6f8767fc5a259&)