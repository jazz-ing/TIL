### 🔖 22.5.3

포크한 레포지토리는 잔디가 심기지 않는다는 걸 알게 된 후로, [이 링크](https://soranhan.tistory.com/11)의 도움을 받아 새로운 레포를 파고 잔디를 심을 수 있었다.  
이후 해당 프로젝트에 수정사항이 생겨 커밋을 하고 원격 레포에 푸시를 했는데 안 되는 거..🤨  
내 git에 등록되어 있는 원격 레포와 내가 푸시하기를 원하는 원격 레포 주소가 다르기 때문이었다.  
새로운 원격 레포지토리를 팠을 때는 당연하게도 새로운 레포 주소로 바꿔줘야한다!  


# 원격 레포지토리 바꾸기

### 1. 원격 레포 확인하기

먼저, `git remote -v` 명령어로 지금 나의 원격 레포지토리 상황을 확인할 수 있다.  

짜잔  

<img width="769" alt="스크린샷 2022-05-03 오후 11 55 16" src="https://user-images.githubusercontent.com/78457093/166478365-d753488d-ebf3-433c-a546-51f759da5ccd.png">

난 앞으로 `nala-market`이 아니라 `ios-nala-market` 레포를 쓸거란 말임~~

### 2. 새로운 URL 등록하기

새로운 Git URL을 등록하려면 아래 명령어를 사용하면 된다.

```swift
git remote set-url origin [새로운 URL]
```

### 3. 원격과 로컬 동기화하기

저장소 주소만 바꾸었기 때문에 원격과 동기화 과정이 필요하다.  
아래 명령어를 써보쟈~

```swift
git remote update origin --prune
```

`update`는 원격의 업데이트를 로컬로 가져오는 명령어, `prune`은 오래된 참조를 삭제하는 명령어다.
update 명령어에서 prune을 함께 써주면 업데이트된 모든 원격에 대해 오래된 참조를 삭제하고, 로컬과 원격을 동기화할 수 있다!

<img width="1082" alt="스크린샷 2022-05-03 오후 11 58 40" src="https://user-images.githubusercontent.com/78457093/166478995-c310989b-0017-4009-a0c3-f7764e1dca21.png">

그러면 완료!

<br>
<br>

> 출처  
> https://git-scm.com/docs/git-remote  
> https://webisfree.com/2020-04-14/[git]-git-remote-repository-%EB%B3%80%EA%B2%BD%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95
