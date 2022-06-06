## 🔖 22.6.6

# 앱 만들기 전엔 .gitignore부터 추가하자

앱을 만들거나 프로젝트를 진행하기 위해 우리는 git을 통해 소스코드를 관리한다.
따라서 코드를 작성할 준비가 됐다면 제일 먼저 하는 일은 git 저장소를 만드는 일이다.
git init이나 clone을 통해서 저장소를 만든 다음 원격 저장소까지 연결하고, 코드 작성을 시작한다.

그런데 여기서 한 가지 빠진 작업이 있다.
바로 **`.gitignore` 추가하기!**

`.gitignore`파일을 추가하는 건 하지 않는다고 당장 앱이 크래시가 나거나 치명적인 문제가 생기는 것도 아니고, 처음 앱 만들기를 배울 때 강의 등에서 강조되는 부분도 아니기 때문에 빠트리기 쉬운 부분이다.

이 `.gitignore`라는 게 무엇이길래 앱을 만들기 전에 파일을 추가하라고 하는건지 차근차근 알아보자.

# 🫥 `.gitignore`란?

`.gitignore`는 **특정 파일들을 버전관리에서 제외하기 위해 Git이 추적하지 않도록 지정해놓는 파일**이다.

어떤 파일을 Git이 관리하는 대상에서 제외하고 싶은 경우, gitignore파일에 추가하는 것이다. 
일종의 파일 목록이라고 볼 수 있다.

# ❓ 왜 `.gitignore`를 추가해야할까?

우리는 Git을 사용해 소스코드의 변화를 기록해서, 문제가 발생하거나 변경사항이 생기면 쉽게 과거로 돌아가 코드를 수정하곤 한다.

따라서 프로젝트에서 사용하지 않는 파일이나 불필요한 충돌을 일으킬 수 있는 파일들은 굳이 커밋하지 않고 아예 Git의 관리 대상에서 제외시켜버리는 것이 소스코드를 관리하기에 훨씬 편리하다.

gitignore를 통해 불필요한 파일들을 Git의 추적에서 제외해주면 소스코드 관리에도 편리하고, 용량도 줄일 수 있다.

# 📁 `.gitignore`에 추가해줄 파일들

위에서 말한 것처럼 ‘프로젝트에서 사용하지 않는 파일이나 불필요한 충돌을 일으킬 수 있는 파일들’은 추가하는 것이 좋다.

그래서 그런 파일이 뭐냐?
- IDE가 생성하는 파일
- 개발 언어, 프레임워크가 생성하는 파일
- Package Manager로 다운로드한 파일 등등

IDE나 개발 언어, 프레임워크가 생성하는 파일들은 대부분 프로젝트가 작동하는 데는 필요하지 않기 때문에 저장소에 보관할 필요가 없다.
Package Manager로 다운로드받은 파일의 경우엔 명령어 한줄(e.g. `pod install`)이면 쉽게 다시 다운로드할 수 있기 때문에 굳이 저장소에 추가하지 않는다.

github에서는 [gitignore 레포지토리](https://github.com/github/gitignore)에 각 IDE나 언어 등에서 생성하는 파일들 중 gitignore에 추가해야 하는 파일들을 정리해두었다.
하지만 여기에서 찾는 것도 귀찮..ㅎ

[gitignore.io](http://gitignore.io)에서는 내가 사용할 IDE나 개발 언어, 패키지 매니저 등을 검색하면 gitignore에 추가할 파일을 자동으로 만들어준다.

예를 들어, CocoaPods를 사용해 SwiftLint 라이브러리를 사용하는 iOS 앱을 만들거라면 `Xcode`, `Swift`, `CocoaPods`을 [gitignore.io](http://gitignore.io)에 검색한다.

![스크린샷 2022-06-06 오후 8 44 29](https://user-images.githubusercontent.com/78457093/172172146-6c6fc0fb-9503-4503-953f-6c9bc54e704f.png)

그러면 아래와 같이 텍스트를 만들어준다. 

![스크린샷 2022-06-06 오후 8 44 46](https://user-images.githubusercontent.com/78457093/172172161-ec422c99-cbe2-4b7f-9772-7484c6d9bb6e.png)

이 텍스트를 그대로 복사 붙여넣기 해서 gitignore파일에 추가해주면 끝!

## `.gitignore` 추가하는 과정 살펴보기

gitignore 파일은 `.git`파일이 있는 프로젝트의 최상위 디렉토리에 있어야하기 때문에 최상위 디렉토리로 먼저 이동한다.

```
$ cat .gitignore
```

이후 터미널에 `cat` 명령어로 파일을 생성한 뒤 gitignore.io에서 생성해준 텍스트를 그대로 복사 붙여넣기 해주면 된다.

그리고 아래와 같이 add, commit, push까지 해주면 완성~

```
$ git add .gitignore
$ git commit -m "chore: .gitignore 파일 추가"
$ git push origin main
```

(커밋을 해주는 이유는 프로젝트를 진행하는 팀원들이 모두 같은 파일을 `.gitignore`로 제외하기 위함이다.)


# 📲 앱을 만들기 전에 추가해주자

`.gitignore`파일은 저장소를 만들고나서 **프로젝트 코드를 작성하기 전에 만드는 것**이 좋다.

이미 git이 추적을 시작한 파일은 gitignore파일에 추가를 해도 추적에서 제외되지 않기 때문에, 제외하고 싶은 파일을 실수로 커밋하면 gitignore에 추가하는 효과가 전혀 없다.

따라서 프로젝트를 시작하는 첫 커밋은 gitignore파일을 추가하는 커밋이 되는 것이 좋다👍


## 만약 `.gitignore`에 파일을 추가하기 전에 커밋을 해버렸다면?

`.gitignore`는 버전관리에서 제외하고 싶은 파일을 untracked상태, 즉 stage에 올리지 않게 해주는 것이기 때문에 이미 stage에 올라간 파일을 unstage 상태로 만들어준 뒤 gitignore에 추가해주면 된다.
unstage하는 git 명령어는 `--cached`~

```
$ git rm --cached [파일이름]

```

특정 파일 하나만 unstage하고 싶은 경우, 위 명령어를 통해 해당 파일을 unstage해주면 된다.

그런데 만약 이미 프로젝트를 너무 많이 진행한 상황이라 파일 하나하나를 unstage할 수 없는 경우엔 어떻게 할까?
이럴 땐 모든 하위 디렉토리까지 지워주는 `-r` 명령어와 현재 디렉토리를 의미하는 `.` 명령어를 써줘서 모든 파일을 unstage해준다.


```
// 이미 여러 파일을 올려서 모든 파일을 unstage하고 싶은 경우
$ git rm -r --cached .
```

완성!

<br>

앞으로는 프로젝트나 앱을 만들 때, 코드를 작성하기 전에 잊지 않고 `.gitignore`를 추가해주자ㅎㅎ

<br>
<br>

> 참고
[https://git-scm.com/docs/gitignore](https://git-scm.com/docs/gitignore)  
[https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring)  
[https://zellwk.com/blog/gitignore/](https://zellwk.com/blog/gitignore/)  
https://stackoverflow.com/questions/5765645/should-you-commit-gitignore-into-the-git-repos  
https://git-scm.com/docs/git-rm  
