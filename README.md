# TIL
오늘 내가 배운 것들(Today I Learned)

### [1일차 학습]
- h : heading 의 약자 
- p : paragraph 의 약자
- head 태그안의 title 태그를 이용해 페이지 제목 설정 가능
- meta
charset="utf-8" 로 인코딩 설정 가능
또는 document.characterSet 으로 html 파일의 인코딩 확인
meta 태그의 경우 contents가 없으므로 닫는 부분이 없음( Empty Element)

- title 속성이 존재함 (처음봤는데, 시간날때 다시 읽어봐야겠다.)
http://blog.hivelab.co.kr/%EA%B3%B5%EC%9C%A0-title-%EC%86%8D%EC%84%B1%EC%9D%98-%EB%B0%94%EB%9E%8C%EC%A7%81%ED%95%9C-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95/
https://nuli.navercorp.com/sharing/blog/post/1132934 ( 사용하지 말라는 의견 )

- html 기본 골격 
반드시 html 안에는 head와 body만 존재하고 표준을 위해 doctype 설정.
또한 대부분의 태그는 소문자이나 doctype의 경우는 대소문자 관계없음.
document.doctype 로 확인 가능

``` html
<!doctype html>
<html>
  <head></head>
  <body></body>
</html>
```

- 언어 : 해당 언어로 음성 출력 가능
``` html
<html lang="ko-KR"> 대한민국의 한국어 
```
|언어|코드|
|---|---|
|한국어|ko|
|영어|en |
|일본어|ja|
|스페인어|es|

- image
alt : alterate text 의 약자 (오류가 발생한 경우 이미지 대체 또는 전맹시각장애자를 위한 접근성준수)

- figure, figcaption 
표, 차트, 이미지를 감싸서 사용

- entitycode
https://entitycode.com/#common-content
https://soye0n.tistory.com/196 (한자 사용 방법, 한글 폰트는 불가능)

- ul , ol 은 반드시 li 요소만 감쌀수 있다. (생각보다 신경쓸게 많다.)

#### 질문
없음

#### 느낌점
나머지 영상도 간단히 살펴보았는데, 내가 모르는 태그나 매우 많았다. 알고 안쓰는 것과 몰라서 안쓰는 것은 큰 차이니 열공!!

항상 영어문서만 봤었는데, mdn한글 문서도 보니 번역이 잘되어 있네, 기계번역이 아닌것 같다.