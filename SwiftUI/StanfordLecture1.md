### 🔖 22.5.16

# SwiftUI

SwiftUI의 가장 큰 장점 중 하나는 UI와 로직을 명확히 구분하는 것!

SwiftUI로 만든 앱은,

- UI code → functional programming
- Model, Logic code → object-oriented programming

## `View`프로토콜을 채택한 `ContentView`

```swift
struct ContentView: View {
    var body: some View {
        Text("Hello, world!")
    }
}
```

⇒ View처럼 **행동**한다.  

### View처럼 행동한다?

- View
    - 스크린의 직사각형 구역.(이 `ContentView`라는 struct(data structure)가 바로 그 직사각형 구역임.)
    - 뷰 안에 뭔가를 보여줄 수 있는 기능이 있음.
    - 사용자의 입력(tap, swipe, pinch같은 multi-touch 이벤트)을 받을 수 있음.
    
    **⇒ 스크린의 직사각형 구역에서의 인풋과 아웃풋**

- View처럼 행동하려면 `body` 변수를 가져야 한다. (타입이 some View인 `body` 변수)

```swift
var body: some View
```

`some View`란? → body 변수의 타입 → View처럼 행동하는 something!

- SwiftUI 앱에서 거의 모든 UI systemdms 'View 안에 View'와 같은 개념으로 만들어진다.
     
    레고처럼 만들어지는 것.   
    예를 들어 레고로 만든 집은 레고 거실, 레고 욕실, 레고 침실 등으로 만들어졌고, 레고 욕실엔 레고 의자와 레고 책상, 레고 의자는 또 작은 레고 블록들로 이루어졌다.  
    레고 거실 역시 그 자체로 레고라는 시각에서, View가 만들어지는 방식을 이해할 수 있다.   
    따라서 View처럼 행동하려면 view같은 some other view 타입의 body 변수를 구현해야 하는 것!!  

#### View의 종류
- Text()는 대표적인 레고 블럭. Rectangle, Circle 모두 레고 블럭인 View.  
- 또다른 파워풀한 뷰로는 combiner가 있다. 다른 뷰들을 combine해서 스크린에 보여주는 뷰. grid 형태로 보여주거나, 한 줄로 보여주거나, 위로 겹쳐서 보여주거나 다양한 형태가 있다.  
- 또 다른 뷰로는 bag of lego. 엄청 큰 레고를 사면 많은 레고 블럭들이 특정 파트별로 여러 그룹들로 레고가 비닐 백에 담겨 있는데 이 비닐 백의 역할을 하는 뷰라고 볼 수 있다.  
  combiner view가 이 bag of lego를 열어보고, 합쳐서 새로운 뷰를 만든다고 볼 수 있다.  
    

## Functional Programming

```swift
var body: some View {
    Text("Hello, world!")
}
```

여기서 Text()를 감싸고 있는 클로저는 **함수**다.  
함수는 일급 시민으로 원하는 어디에나 쓸 수 있다. functional programming에서 함수는 정말 어디에나 있다.  
이 클로저(함수)는 Text(또 다른 some View. some View 타입인 body의 리턴값으로 적절)를 **리턴**하고 있다.  

### 그럼 왜 처음부터 Text타입으로 안 쓸까?
```swift
var body: Text {
    Text("Hello, world!")
}
```
위와 같이 작성해도 빌드에 성공하는데, 왜 처음부터 Text라고 쓰면 안 될까?  
위에서 말했듯, SwiftUI는 '뷰 안의 뷰'와 같은 방식으로 UI를 구성하고 이를 functional programming을 통해 구현한다.  
여러 함수를 실행시키면서 계속해서 다른 타입의 View가 리턴될 것이기 때문에 코드가 더 복잡해질 것이고, 이를 컴파일러가 판단하도록 하는 것이다.  

`body`변수를 생각해보자.  
`body`변수는 실제로 메모리에 저장되지 않는다. 실행되는 함수에 의해 계산되는 변수이다.  
some View라는 타입은 진짜로 실제 타입이라기보다 컴파일러에게 '이 변수가 어떤 View 타입이 될거니까 이 함수를 실행해서 안의 과정을 계산해 실제로 어떤 View인지 알아봐줘!'하면 컴파일러가 함수 실행결과로 Text라는 View로 바꿔주는 것이다.  

예를 들어,  

```swift
var body: some View {
    return Text("Hello, world!")
            .padding()
}
```

이렇게 `padding()`이란 modifier 함수는 View처럼 행동하는 something을 리턴하고 있다.  
padded View를 리턴하고 있는 것 → 확실히 Text 타입은 아니다.  
컴파일러가 `body` 변수의 클로저, 즉 함수를 실행해 연산해서 padded View를 반환하고 있는 것이다. 따라서 some View라는 타입을 쓴다!  


### Shape 종류의 View

```swift
var body: some View {
    return RoundedRectangle(cornerRadius: 25.0)
}
```

`RoundedRectangle(cornerRadius: 25.0)`도 Text와 같은 또 다른 레고 블럭이다.  
shape들은 또다른 기능이 있음 → `stroke()`  
Text는 view지만 shape가 아니라 `stroke()`를 실행하지 못한다.

### Combiner View (e.g. ZStack)

```swift
var body: some View {
    // ZStack(content: () -> _)
    ZStack {

    }
}
```

Zstack의 `content`인자는 함수다. functional programming again!!  
이 함수는 결국 **bag of lego를 리턴**할 것이다. ZStack에게 bag of lego를 주는 것.  

Swift는 우리가 개발을 하면서 bag of lego를 정말 많이 쓸 것을 알기 때문에! 이 과정을 매우 쉽게 만들어두었다ㅎㅎ  
이렇게 bag of lego를 만들어 lego combiner view에게 주는 함수를 View builder라고 한다.  

이 함수는 다른 뷰들을 나열하게 해주고, bags them up into a bag using this function and returns it해서 ZStack이 작업할 bag of lego를 가질거다.
bag of lego 안에서 조건문도 가질 수 있고 변수도 정의할 수 있다.

### Modifier on Combiner View

view combiner에 modifer를 적용하는건 어떤걸까?

- padding()
    
    zstack 안의 view에는 패딩이 생기지 않고 zstack자체에 패딩이 생김
    
- foregroundColor
    
    zstack안의 모든 view에 해당 색이 적용됨. zstack은 그리는 게 아니기 때문에 안의 그리는 요소에 적용되는 것. 
    
    안의 요소에 foregroundColor를 적용하면 해당 view에 직접 준 설정이 적용된다. zstack에 준 색은 디폴트 컬러로 작용하는 것.
