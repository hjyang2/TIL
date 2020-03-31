# TIL
오늘 내가 배운 것들(Today I Learned)

### [2일차 학습]

- href 의 #, #top은 최상단이며 보통 id를 사용 (다만 습관적으로 id 사용에 거부감이 존재)

- a태그 모질라 페이지를 보니 모르는 부분이 많다. 나중에 자세히 봐야겠다.
  
  a 요소는 사용자의 보안과 개인정보에 중요한 영향을 줄 수 있습니다. Referer 헤더: 개인정보와 보안 고려사항 문서에서 자세한 내용을 알아보세요.
  
  target="_blank"를 rel="noreferrer"와 rel="noopener" 없이 사용하면 웹사이트가 window.opener API 악용 공격에 취약해집니다. (취약점 설명).
  
  onclick 이벤트
  앵커 태그의 href를 "#"이나 "javascript:void(0)"으로 지정해 페이지 새로고침을 막고, click 이벤트 처리기를 등록해서 가짜 버튼을 만드는 방식으로 남용하는 경우도 많습니다.
  이런 가짜 href 값은 링크를 복사하거나 드래그할 때, 링크를 새 탭이나 새 창에서 열 때, 즐겨찾기에 추가할 때와 더불어 JavaScript를 불러오는 중일 때, 오류가 발생했을 때, 아니면 JavaScript를 비활성화했을 때 예측하지 못한 동작을 하게 만듭니다. 또한 스크린 리더 등 보조 기술에도 잘못된 의미를 전달합니다.

  \<button\> 을 대신 사용하세요. 하이퍼링크에는 진짜 URL로의 내비게이션만 사용하면 됩니다.
  https://www.jitbit.com/alexblog/256-targetblank---the-most-underestimated-vulnerability-ever/

- 설명 
설명 목록(dl : description List) =  용어(dt : term) + 해당 용어에 설명내용(dd : description)
태그 속성에 값에 넣는 문자는 entitycode 로 할 필요 없음
img에 title 속성을 통하여 툴팁 가능

- 인용과 줄바꿈
인용 : \<q\> quotation ( cite 속성 사용 가능)
인용단락(긴 인용문) : \<blockquote\> blockquote
출처 : \<cite\> citation
\<br\>은 linebreak 용도로 사용하고 두번사용해서는 안됨.
 

- 어휘 요소들
아래 두가지를 구분해야 함 (즉 bold 가 의미적으로 강조가 아니다.)
1)강조 : sematic
2)표현적인 목적 : Non sematic
\<strong\> 중요성, 심각성 , 긴급성


- 섹션 메인
\<body\> ( root section 이라고 부름)  
\<body\>  
\<header\> :  \<nav\> 
\<main\> : \<aside\>, \<section\> ( 큰 카테고리 분류, section 안에는 \<article\> 을 이용해 다시 분류) 
\<footer\> :  저자, 링크, 저작권 정보

- section
섹션요소는 일반적인 컨테이너 요소(단순 Grouping을 우한 목적)가 아니며, 문서개요에 명시적으로 나열할 수 있는 컨텐츠에만 적합  
=> 일반적인 컨테이너 요소는 div, span 사용, 반드시 목차에 해당되는 컨텐츠에 적합
반드시 헤딩(h1~h6) 요소가 필요
일반적인 섹션을 의미(소개, 뉴스 항목들, 연락처 정보)

- article
헤딩(h1~h6) 요소가 필요 
독립적인 섹션을 의미( 잡지, 신문, 에세이, 보고서 , 블로그, 기타 소설미디어...)
<참고>
article 내부에 section을 포함할 수도 있고, section 내부에 article을 포함 할 수도 있다.
콘텐츠가 사이트에 포함된 독립적인 섹션의 성향이 크다면 section 요소 대신 article 요소를 사용하는 것이 좋다. 

- aside :웹사이트의 사이드바에 해당되는 부 콘텐츠 섹션을 말한다.
- nav : 다른 페이지로 이동하는 링크 또는 사이트 내 탐색 링크를 포함하는 섹션 요소이다.
<참고>
내용을 쉽게 이해할 수 있도록 nav 요소 내부에는 비순차 목록(ul)을 사용한다. 
사이트의 모든 링크를 nav 에 포함하는 것은 아니며, 주로 사이트를 탐색하는 링크를 포함한다. 
사이트 하단에 위치한 링크는 footer요소로도 충분하다. 

- main
main 요소는 섹션요소가 아니며, main은 반드시 1개만 보여져야 하므로, hidden 속성을 이용해야 한다. 
\<main> \</main>
\<main hidden> \</main> 
<참고>
article, section, aside, nav 는 main요소를 자식으로 포함할 수 없다. 
반대로 main요소는 섹션(article, section, aside, nav)요소들을 포함할 수 있다. 
main 내부에는 header, footer 요소를 직접적으로 포함하지 않는다. (섹션 내부에 footer와, header을 넣는다.)
body 안에는 직접적으로 header, footer 요소를 직접적으로 포함 가능.



#### 질문
1. 시멘틱 태그가 너무 많아 실제로 적용시키기 쉽지 않을 것 같습니다. 시멘틱 태그도 꼼꼼히 작성하는 것을 웹 표준, 웹 접근성(?) "준수"라고 표현하는 것 같은데 실제 웹사이트가 웹 표준이나 접근성이 지켜지지 않을 경우 어떤 불이익이 있는지 궁금합니다. 

#### 느낌점
과제가 많이 늦었습니다!

---

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