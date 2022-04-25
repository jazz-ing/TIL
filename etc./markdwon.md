🔖 22.4.25  
오늘은 Github Profile Readme를 작성했다.  
[Github Readme 꾸미기 총정리](https://velog.io/@seondal/Github-Readme-%EA%BE%B8%EB%AF%B8%EA%B8%B0-%EC%B4%9D%EC%A0%95%EB%A6%AC)라는 글을 참고해서 꾸며봤는데 Readme를 쓸 때마다 마크다운 문법을 찾아보는 게 번거로워서 한 번에 정리해보기로!

# Markdown
[markdown이란?](#markdown이란?)  

[Syntax](#Syntax)
1. [제목](#제목)
2. [인용](#인용)
3. [리스트](#리스트)
4. [구분선](#구분선)
5. [링크](#링크)
6. [강조](#강조)
7. [이미지](#이미지)
8. [줄바꿈](#줄바꿈)
9. [표](#표)
10. [코드 작성](#코드-작성)
11. [링크 목차](#링크-목차)
12. [토글](#토글)
13. [체크박스](#체크박스)
14. [주석](#주석)

## markdown이란?

> **마크다운**(Markdown)은 일반 텍스트기반 의 경량 마크업 언어다. 일반 텍스트로 서식이 있는 문서를 작성하는 데 사용되며, 일반 마크업 언어에 비해 문법이 쉽고 간단한 것이 특징이다. HTML과 리치 텍스트(RTF) 등 서식 문서로 쉽게 변환되기 때문에 응용 소프트웨어와 함께 배포되는 README 파일이나 온라인 게시물 등에 많이 사용된다. (출처: 위키백과)

간단히 말하면, 웹에서 문서를 작성할 때 **문서의 구조를 표현하게 해주는 간단한 언어**다!

## Syntax

### 제목

```
# This is an H1
## This is an H3
###### This is an H6
```

# This is an H1

## This is an H2

###### This is an H6

```
This is an H1
=============

This is an H2
-------------
```

This is an H1
=============

This is an H2
-------------

### 인용

```
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.
```

> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.토글, 밑줄, 표, 이미지, 체크박스

### 리스트

```
*   전부
+   다
-   똑같음
	- 이건 들여쓰기
```

*   전부

+   다

-   똑같음
    - 이건 들여쓰기

```
1.  Bird
2.  McHale
3.  Parish
```

1.  Bird
2.  McHale
3.  Parish

### 구분선

```
* * *
***
*****
- - -
---------------------------------------
```

* * *

***

*****

- - -

---------------------------------------

### 링크

```
[🏄‍♀️룰루날라 Velog](https://velog.io/@nala)
```

[🏄‍♀️룰루날라 Velog](https://velog.io/@nala)

### 강조

```
*이탤릭체*
_이탤릭체_
**볼드체**
__볼드체__
~~취소선~~
<ins>밑줄</ins>
```

*이탤릭체*
_이탤릭체_
**볼드체**
__볼드체__
~~취소선~~
<ins>밑줄</ins>

### 이미지

```
![엑박뜰 때의 이미지 이름](이미지주소)](링크주소)

![초록색사과](https://user-images.githubusercontent.com/78457093/165121142-2666996b-e1ff-4fc0-aadd-a7e9da34903a.jpg)

<img src="https://user-images.githubusercontent.com/78457093/165121142-2666996b-e1ff-4fc0-aadd-a7e9da34903a.jpg" width="200" height="200">
```

![초록색사과](https://user-images.githubusercontent.com/78457093/165121142-2666996b-e1ff-4fc0-aadd-a7e9da34903a.jpg)

<img src="https://user-images.githubusercontent.com/78457093/165121142-2666996b-e1ff-4fc0-aadd-a7e9da34903a.jpg" width="200" height="200">

### 줄바꿈

```
문장 마지막에서 두 칸을 띄어쓰기 하든가  
요런 애를 <br>써도 된다
```

문장 마지막에서 두 칸을 띄어쓰기 하든가  
요런 애를 <br>써도 된다

### 표
```markdown
| 왼쪽 정렬 | 중앙 정렬 | 오른쪽 정렬 | 그냥 쓰면 왼쪽 정렬 |
| :--- | :---: | ---: | --- |
| 수성 | 금성 | 지구 | 화성 |
| 목성 | 토성 | 천왕성 | 해왕성 |
```

| 왼쪽 정렬 | 중앙 정렬 | 오른쪽 정렬 | 그냥 쓰면 왼쪽 정렬 |
| :-------- | :-------: | ----------: | ------------------- |
| 수성      |   금성    |        지구 | 화성                |
| 목성      |   토성    |      천왕성 | 해왕성              |

### 코드 작성

````
```swift
Swift 짱
```
````

```swift
Swift 짱
```

### 링크 목차
````
[토글로 이동](#토글)
````
[토글로 이동](#토글)

### 토글

~~~markdown
<details><summary>CLICK ME</summary>
<p>

#### 코드까지 숨길 수 있다!

    ```
      print("Hello, world!")
    ```

</p>
</details>
~~~

<details><summary>CLICK ME</summary>
<p>

#### 코드까지 숨길 수 있다!

    ```
      print("Hello, world!")
    ```

</p>
</details>

### 체크박스

```
- [x] 할 일 완료 🎉
- [ ] 이건 아직 못 했다.
```

- [x] 할 일 완료 🎉
- [ ] 이건 아직 못 했다.

#### 주석

```
<!-- 주석이라 안 보인다~ -->
```

<!-- 주석이라 안 보인다~ -->

문법의 출처는 [공식사이트](https://daringfireball.net/projects/markdown/syntax), [GitHub Flavored Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)에서~

