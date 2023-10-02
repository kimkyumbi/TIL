# 231002-1 / SWIFT / Picker

Picker는 선택을 편하게 할 수 있게 해주는 것이라고 생각하면 된다.

```swift
struct Day27: View {
    
    @State var isPicked: Int = 0
    
    var body: some View {
        VStack {
            Text(isPicked.description)
            
            Picker(selection: $isPicked, 
                label: Text("Picker")) {
                Text("1").tag(1)
                Text("2").tag(2)
            }
        }
    }
}
```

위 코드는 Picker를 간단하게 구현한 것이다.

State를 이용해 Picker를 눌렀을 때 잘 바뀌었는지 확인할 수 있다.

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1158384242909265980/2023-10-02_9.45.14.png?ex=651c0ce5&is=651abb65&hm=cd83a4cddf2e10d1b46c49c53acc757d77e4beeda161c29d969fe597cce23b16&)

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1158383843238219887/2023-10-02_9.43.33.png?ex=651c0c85&is=651abb05&hm=a4d1473a0293481f27512185a72e74ee4ea1398aed7a5df1709ad666debf74b1&)