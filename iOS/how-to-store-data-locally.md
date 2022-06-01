## 🔖 22.6.1

# 앱에 데이터를 저장하는 방법들

iOS에는 앱에 데이터를 저장하기 위한 여러가지 방법들이 있다.

- UserDefaults
- Keychain
- FileManager
- SQLite
- CoreData

각 방법마다 사용하기 좋은 상황들이 다르기 때문에 어떤 데이터를 저장하고 싶냐에 따라 적절한 기술을 선택해야 한다.

이전엔 ‘이런게 있구나~’하고 넘어갔었는데 이번에 앱을 만들기 시작하면서 서버 없이 로컬로 앱의 데이터를 저장하는 방식을 고민하다보니 여러 방법들에 대해 차이점을 더 자세히 알아보았다.

하나씩 공부해보자!

## UserDefaults

**사용자의 기본 설정 정보를 저장하는 데이터베이스**라고 보면 간단하다.

UserDefaults라는 이름 그대로 ‘사용자의 기본 설정’을 저장하는 용도이기 때문에 작은 정보(예: 사용자가 라d이트모드를 선호하는지 다크모드를 선호하는지, 매일 알림을 받고 싶은 시간, 실제로 알림을 받고 싶은지 등)를 저장하는 데 사용해야 한다.  

<img src="https://user-images.githubusercontent.com/78457093/171413657-f7382201-76bb-49e6-9e76-b1906c4f9a75.PNG" width="200">

아이폰의 설정 앱에서 ‘사운드 및 햅틱'에 들어간 화면이다.  
무음 시 진동이 울리도록 설정을 해두었는데 만약 이 정보를 저장하지 않으면 무음일 때 진동이 안 울려 전화가 오는걸 알아채지 못할 것이다.  
iOS에서는 이렇게 사용자의 설정값들을 UserDefaults에 저장한다.  
따라서 사용자가 만들어내는 많은 양의 데이터를 저장하기에는 적합하지 않다.  

내부적으로는 모든 값이 plist에서 유지관리된다.  
plist에 간단한 데이터 타입(strings, numbers, dates, boolean, urls, datas 등)을 저장하도록 설계되어 plist로 디스크에 저장된다.  

파일이 전체로 읽고 쓰여지기 때문에 UserDefaults를 사용해 부분적으로 변경이 있는 많은 양의 데이터를 저장하면 많은 시간을 낭비하게 된다.  

## Keychain
비밀번호, 신용카드 정보, 인증서 , 들키기 싫은 메모처럼 안전하게 저장하고 싶은 작은 데이터를 저장하는 암호화된 데이터베이스다.

키체인은 디스크의 특수파일로 하드웨어로 암호화되어 있으며, low level의 API가 많다.

실제로 앱에서 키체인을 사용해야하는 경우에는, 복잡한 과정은 좋은 라이브러리를 통해 수행하는 것이 훨씬 간단하다.

## File Manager
아이폰의 file system에 대한 인터페이스로 iOS 앱의 파일을 읽고 쓸 수 있도록 해준다.  

모든 유형의 파일을 파일 시스템에 직접 저장할 수도 있다.   
그러나 보안상의 이유로 앱 컨테이너 내의 파일 시스템에만 액세스할 수 있다.  
기본적으로 앱 컨테이너에는 세 개의 폴더가 있다.  

- Document: 사용자가 생성하는 콘텐츠를 저장하기에 완벽한 장소입니다. iCloud에도 자동으로 백업됩니다.
    - Documents/Inbox: 이것은 다른 앱이 우리 앱에 파일을 열도록 요청할 때마다 시스템에 의해 생성되는 특수 폴더입니다. 이 폴더는 앱의 관점에서 읽기 전용입니다. 예를 들어 메일 프로그램은 앱과 연결된 이메일 첨부 파일을 이 디렉토리에 배치합니다.
- Library: 이 폴더에는 사용자가 생성하지 않은 파일과 앱 실행 사이에 지속되어야 하는 파일을 넣을 수 있습니다. 그러나 장치에 여유 공간이 충분하지 않으면 일부 파일이 삭제될 수 있습니다. 라이브러리 폴더에는 다른 용도로 사용되는 일부 하위 폴더가 있습니다.
    - Library/Caches: 이것은 특수 폴더입니다. 여기에서 곧 필요할 수도 있는 파일을 저장할 수 있지만 잃어버릴 염려는 없습니다. 이러한 파일의 사용을 중단하면 시스템에서 파일을 삭제합니다. 앱을 더 빨리 로드하기 위해 다운로드한 이미지는 이 폴더에 있어야 합니다.
- tmp: 이 폴더에는 앱에 일시적으로 필요한 파일을 저장할 수 있습니다. 앱이 실행되지 않을 때 운영 체제에서 삭제할 수 있습니다.

## SQLite
앱에서 쓰이는 가장 표준적인 데이터베이스이다.  
애플리케이션이 관계가 있는 많은 양의 데이터를 처리하는 경우 SQLite를 살펴볼 수 있다.  
서버리스, 구성이 필요 없는 트랜잭션 SQL 데이터베이스 엔진으로 즉, 애플리케이션에 포함되어 있어 매우 빠르다.  

SQLite는 C로 작성되어 모든 API가 C 언어로 되어 있다.  
SQLite와 Objective C 사이의 간격을 메우기 위해 시간이 지남에 따라 많은 ORM(Object Relational Mapping)이 만들어졌다. 

데이터의 양이 많고 잘 구조화되어있는 경우에 적절하게 사용될 수 있다.  
저장 기능 외에도 효율적인 검색이 가능하고 복잡한 쿼리를 작성할 수 있다.   

## Core Data

Apple의 persistence 솔루션인 Core Data를 사용하면 애플리케이션이 모든 형식의 데이터를 저장하고 다시 가져올 수 있다.  
Core Data는 일반적으로 데이터를 하나(정확히 말하면 SQLite 데이터베이스)에 저장하지만 기술적으로 데이터베이스는 아니다.  
ORM(객체 관계형 매퍼)도 아니지만 ORM처럼 느껴질 수 있습니다.  
제대로 말하면 **객체 그래프**로, attribute와 다른 객체에 대한 relationship이 있는 객체를 생성, 저장 및 찾아올 수 있다.  
단순함과 강력함을 통해 기본 데이터 모델에서 복잡한 형식에 이르기까지 모든 형식의 데이터를 저장할 수 있다.  

코어 데이터는 저장 기능 외에도 실행 취소 및 다시 실행 작업을 수행할 수 있다.  
또한 성능이 매우 우수하며 데이터를 검색하고 찾아오는 시간이 매우 빠르다.  



> 참고
> [https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/AboutPreferenceDomains/AboutPreferenceDomains.html](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/AboutPreferenceDomains/AboutPreferenceDomains.html)  
[https://medium.com/@imranjutt/data-persistence-in-ios-2804d04bde62](https://medium.com/@imranjutt/data-persistence-in-ios-2804d04bde62)  
[https://betterprogramming.pub/5-ways-to-store-user-data-in-your-ios-app-595d61c89667](https://betterprogramming.pub/5-ways-to-store-user-data-in-your-ios-app-595d61c89667)  
