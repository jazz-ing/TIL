### 🔖 22.4.27

# 레포지토리에서 폴더명 바꾸기

캠프에서 진행한 프로젝트들을 하나의 레포지토리에 정리하던 중, 레포지토리의 폴더명을 바꾸고 싶어졌다.

`git 레포지토리 폴더 생성`과 같은 검색어로 구글링을 하니 대부분 아래와 같은 방식으로 바꾸는 방법만 나왔다.

![til_0427](https://user-images.githubusercontent.com/78457093/165536783-4fba2a2b-e01e-4b8c-844b-def9e22e29c3.gif)

이렇게 해도 폴더명을 바꾸는 게 가능하긴 하지만, 파일 단위로 하나하나 바꿔줘야하기 때문에

해당 파일에 하위 폴더와 파일이 많았던 나의 경우에는 정말 정말 번거롭고 시간이 오래 걸리는 작업을 해야했다.

한 번에 바꿀수는 없나!! 찾아보던 중 단비같은 명령어를 알게 됐다.

바로 **✨`git mv`✨**

## git mv

**파일이나 폴더를 이동하거나 이름을 바꿀 수 있는 명령어**로, 원하던대로 폴더 이름을 한 번에 바꿀 수 있었다.



```
git mv 변경전이름 바꾸고싶은이름

// example
git mv BankManagerConsoleApp BankManager
```



폴더 이름을 바꿨으니 원격 저장소에까지 반영시키기 위해 `add`와 `commit`, `push`를 차례대로 해야할 것 같지만,

이때 `add`는 생략해도 된다.



사실 `git mv`를 하는 것은 아래와 같은 거기 때문!

```
mv BankManagerConsoleApp BankManager
git rm BankManagerConsoleApp
git add BankManager
```



앞으로도 유용하게 쓸 수 있겠다😋

<br><br><br>

> 출처
>
> https://git-scm.com/docs/git-mv
>
> https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0

