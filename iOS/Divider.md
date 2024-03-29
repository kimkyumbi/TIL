# 231011-1 / SWIFT / Divider

Divider는 하나의 `Contents`와 다른 `Contents`를 구분해주는 뷰이다.

각설하고 예제만 보도록 하자

```swift
var body: some View {
     //VStack으로 전체 화면을 40으로 할당
    VStack(spacing: 40){
        Group {
            //H_Divider
            Text("Horizontal Divider")
            Divider()
            Image(systemName: "a.circle.fill")
            Divider()
        }
    }
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1164064002515677284/2023-10-18_1.54.37.png?ex=6541da15&is=652f6515&hm=8a9609086c1d8174a99dbee15db3f90b092bf3864cc1af0883d40881e062960c&)

이렇게 나오게 된다. 

```swift
// 나머지 코드들

Group {
    //2. V_Divider
    Text("Vertical Divider")
    //HStakc으로 가로 정렬
    HStack {
        Divider()
        Image(systemName: "b.circle.fill")
        Divider()
        //구분선 길이 조절
    }.frame(height: 100)
}
Group {
    //3. 색상
    Text("Divider 색상")
    Divider()
        .background(Color.red)
    Image(systemName: "c.circle.fill")
    Divider()
        .background(Color.red)
}
Group {
    //4. 길이
    Text("Driver 길이 조절")
    Divider()
     //frame 으로 길이 조절
        .frame(width: 200)
    Image(systemName: "d.circle.fill")
    Divider()
        .frame(width: 300)
}
```

![image](https://cdn.discordapp.com/attachments/1147333501696364555/1164065132033364038/2023-10-18_1.58.44.png?ex=6541db22&is=652f6622&hm=f0e6efac270fb12a9344641387f8cbfcabad2bed7f5cdcbc6a390db6ca56f132&)

결과적으로 이렇게 나온다.