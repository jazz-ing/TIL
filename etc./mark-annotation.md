### 🔖 22.4.26

예쁜 코드를 보면 기분이 좋아지고 뇌에서 도파민이 분비되는 것 같다..ㅋㅋㅋㅋㅋㅋㅋ  
읽기 쉽고 예쁜 코드를 작성하기 위한 방법에는 `Mark 주석`을 활용하는 것이 있는데 오늘은 그것에 대해 정리해봤음!🤓

<br>

# Mark 주석으로 예쁘게 코드 섹션 나누기

우리는 `jump bar`라는 걸 사용해서 원하는 파일, 원하는 프로퍼티나 메소드 등으로 바로 이동할 수 있다.

바로 이게 jump bar!  
<img width="766" alt="jumpBar" src="https://user-images.githubusercontent.com/78457093/165325663-4616ea92-ab3c-4729-9de7-90e1224b5352.png">

이 jump bar를 활용하면  
<img width="766" height="500" alt="jumpBar" src="https://user-images.githubusercontent.com/78457093/165325427-2fc8f104-bb3c-459b-8be6-f723f68e1732.gif">  
요렇게 바로 바로 파일을 이동할 수 있다ㅎㅎ

Xcode를 쓸 때마다 보고, 자주 사용하기도 하지만 이름이 jump bar라는 건 처음 알았다. 식빵 봉지 묶는 철사 이름이 뭔지 모르는 것처럼ㅋㅋㅋㅋ  

Mark 주석은 바로 이 jump bar에서 섹션을 나눠 코드의 가독성을 높여주는 기능이다.  
`// MARK: 주석 내용 쓰기`와 같이 코드에 주석을 작성하면 jump bar 상에 섹션이 나눠져 표시된다.  
바로 요로케  
|전|후|
|---|---|
|<img width="199" alt="beforeMark" src="https://user-images.githubusercontent.com/78457093/165326355-b0b57d73-7e99-4669-9ed3-c6a993dbc6a0.png">|<img width="191" alt="afterMark" src="https://user-images.githubusercontent.com/78457093/165326908-c09b8e1d-089c-4370-9265-869e93e722dd.png">|

훨씬 깰-끔하다😎



코드가 복잡해질수록 파일도 많아지고, 한 파일의 코드도 굉장히 길어져서 어떤 프로퍼티나 메서드가 있는지 확인하기가 어려워진다.

원하는 아이템의 이름을 정확히 안다면 `command+f`나 `command+shift+f`로 바로 찾을 수 있지만 정확히 이름을 알지 못해 검색할 수 없거나,  
한 눈에 코드의 형태를 보고싶은 경우에는 이 jump bar가 아주 유용하다!

## `// Mark:`만 있는게 아니지 훗
Mark 주석 외에도 To-do나 Bug fix관련한 기능도 있다!

#### To-do item

```swift
// TODO: 무엇을 구현할까요
```

#### Bug fix reminder

```swift
// FIXME: 버그를 잡자!
```

#### Heading

```swift
// MARK: 줄 안 긋기
// MARK: - 줄을 그어 구분하고 싶다면 하이픈 추가
// MARK: 아래에 줄을 긋고 싶다면 뒤에다가 하이픈 -
```
|코드|점프 |
|---|---|
|<img width="592" alt="annotationCode" src="https://user-images.githubusercontent.com/78457093/165328766-c833300c-25c3-4ed5-a497-ac16010b7286.png">|<img width="228" alt="annotationJumpBar" src="https://user-images.githubusercontent.com/78457093/165328740-dd2eafd6-00f6-455f-b022-e79b47b6e4a6.png">|

<br>
<br>
<br>

>  출처
>
> - https://help.apple.com/xcode/mac/current/#/dev86a148f73
> - https://stackoverflow.com/questions/24017316/pragma-mark-in-swift
