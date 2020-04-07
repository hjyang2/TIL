# TIL
오늘 내가 배운 것들(Today I Learned)

### [7일차 학습]

#### 상속

- 상속 되는 속성(글자색, 글자 디자인에 관련된 것)
    - color, font-size , font-family, letter-spacing, strong

- 상속되지 않는 속성(공간에 관련된 것)
    - outline, margin, border, padding

#### 우선적용 규칙
- 요소 선택자(0,0,0,1) < 클래스 선택자(0,0,1,0) < ID 선택자(0,1,0,0) < 인라인 스타일(1,0,0,0) 
- *, >, +, ~ 등의 콤비네이터와 :not() 가상클래스는 특성에영향을 주지 않는다.
- 아래는 예시(한번씩 눈으로 확인해보자)
    - \* ---- 0000
    - a ---- 0001
    - a.link ---- 0011
    - li:nth-child(2) a:hover ---- 0022
    - .nav:nth-child(2) a:hover ---- 0031
    - #outer a ---- 0101
    - #outer #inner a ---- 0201
    - style="color: tan" ---- 1000
- Q : class 속성 개수가 11개면 id 속성 보다 우선할까요? 
    - A : class 속성 값의 개수가 아무리 많아도 id 속성 보다 중요성이 떨어짐.
    - Importance
    - Specificity
    - Source order

- Typography
    - 폰트에 영향을 주는 속성
        - font-family, font-size, font-weight, font-style, color
        - color 를 표현하는 방법 : color keyword, hex color, rgb color, hsl(180,50%,60%, 1)
    
    - 웹 안전 폰트
        - Arial 고딕(sans-serif)
        - Verdana 고딕(sans-serif)
        - Courier New 코드체(공간이 동일)(monospace)
        - Georgia 명조체(serif)
        - Times New Roman 명조체(serif)
        - Trebuchet MS 명조체(serif)

    - 저작권 없는 폰트 
        - fonts.google.com

    - text 레이아웃 속성

        - line-height 행간 (기본값 : 1.25)
        - letter-spacing 자간 ( 기본값은 : 0)
        - word-spacing 어간 : 단어사이 간격
        - text-align 
        - text-indent 들여쓰기 
        - text-transform : uppercase,  lowercase
        - font-variant: small-caps(대문자는 큰 대문자, 소문자는 작은 대문자), all-small-caps(모두 작은 대문자로 변경) ( 한글은 당연히 적용 안됨)
        - text-decoration : underline overline line-through(\<s>\</s>)
        

        - white-space : nomal -> 기본값
        - white-space : pre -> 입력한 그대로
        - white-space : pre-line -> 들여쓰기만 제거
        - white-space : norwap -> 한줄로 길게 쓰임( 줄바꿈 문자를 인식 안 하는듯?)
        
        - word-break : 단어의 분리를 어떻게 할 것인지 결정
        - word-wrap : 박스의 가로 영역을 넘친 단어 내에서 임의의 분리 여부를 결정하여 불바꿈 관여
        
        - text-shadow : 4px 4px 0px #9bdbde (x, y, blur, spread, color) ( 멀티도 가능함)

#### 정리사항
- !important 가능하면 사용하지 말자.
- 가상 클래스도 클래스이므로 우선적용 규칙에서 "10 point" 적용.
- woff = web open font format 
- line-height 은 가능한 1.5 이상
- 자간보단 어간이, 어간보단 행간이 커야한다.

#### 질문
- 개발을 하다보면 "고객측이 브라우저 확대/축소도 고려해야 하지 않느냐?"고 이야기 할 때가 있습니다. (반응형이 아니라 ctrl 누른 상태에서 마우스 스크롤로 변경하는 브라우저 확대/축소 입니다.)
- 질문 1 : 보통 확대 / 축소에서 문제가 되는 부분은 축소이고, 이때 어디까지 고려하는지 궁금합니다. ex) 90, 80, 75, 67, 50% ..
- 질문 2 : 관련 문제를 해결하면서 저는 이제 font는 rem 단위로 padding, margin 등의 font크기에 영향받는 부분은 em 단위로, line-height 는 1.2같은 비율로 적용하라고 합니다. 혹시 이와같은 방법이 맞는 해결인지 궁금합니다. 아니라면 어떤 부분을 고려해야하는지 궁금합니다.


#### 느낌점
- 크롬 개발자 도구에서 불투명한 css는 상속받은 것이 아니다. (체크가 되어 있어도 적용된 것이 아니다.)

---

<details>
<summary> 6일차 학습</summary>

#### CSS

- 표준화 단계
    - FPWD	First Public Working Draft
    - WD	Working Draft
    - CR	Candidate Recommendation
    - PR	Proposed Recommendation
    - REC	Recommendation
    - SPSD	Superseded Recommendation

#### 기본 문법

- 구성 : 대상 선택자, 속성, 값, 
- 적용 방식

    1. Internal Style  : html 코드에 직접 작성하는 방식으로 body가 아니라 head 태그에 넣어야 한다. 또한 MIME type은 생략 가능
    2. Inline Style : 요소 내부에 인라인 형태로 작성
    3. External Style link 요소로 사용
    ```html
    <link href="css/style.css" type="text/css" rel="stylesheet"/>
    ```
#### 선택자

- 심플 선택자 
    - 종류 : element type selector, Grouping selector, Universal selector, class selector(단락요소), multi class selector, id selector,  descendant selector

- Attrivute Selector (속성 선택자)
    - img[alt*="css"] 
    ```html
    <abbr alt="htmlcssjavascript" src="love.jpg" >
    ```

    - [shape][title] 
    ```html
    <area shape="" coords="" href="" title="">
    ```

    - 아래는 모두 태그는 관계 없이 작동 ( 정규표현식과 비슷하게 작동)
    ```css
    [href^="http://"] { ... }
    [src$=".svg"]     { ... }
    [src*="phone"]    { ... }
    ```

- 가상 클래스

    - :link         { ... }
    - :visited      { ... } 

    - :hover        { ... }
    - :active       { ... } : 선택시 작동

    - :focus        { ... } : 키보드 속성
    - :focus:hover  { ... }
    - :focus:active { ... }

    - :first-child  { ... }
    - :last-child   { ... }
    - :nth-child(n) { ... } : even, odd 사용 가능, n은 1이 아니라 10터 시작됨.
    https://developer.mozilla.org/ko/docs/Web/CSS/:nth-child
    - :lang(ko)     { ... } : 보통 font 변경시 사용

- 가상 요소 선택자(Pseudo Element)
  - :: 2개가 가상 요소
  - 종류
    - ::first-letter {...}
    - ::first-line {...}
    - ::before {...}
    - ::after {...}
  
#### 정리사항
- 네트워크 탭으로 css 불러왔는지 확인하고 파일 이름이 붉은색이면 이상 상태
- user agent stylesheet 는 웹브라우저가 기본적으로 제공하는 것
- abbr 태그를 사용하고 그때 title 속성으로 툴팁을 사용
- class 의 경우 속성 선택자를 사용하면 정확히 일치되지 않거나, 순서가 바뀐경우 인식을 못한다. 항상 class 선택자를 사용하자. 

    ```html
    <p class='note box'></p> <!-- 불일치 -->
    [class="note"] {...} 
    <p class='box note'></p> <!-- 불일치 -->
    [class="note box"] {...}
    ```
- html 과 다르게 css는 대소문자 구분
- parent:nth-child(n) : 부모의 n번째 자식이라는 의미
- element:nth-of-type(n) : 같은 유형(element)의 n번째 형제라는 의미
 
  
#### 질문

- 개인적으로 before/ after 이용해서 원이나 삼각형을 문장 앞에 사용하곤 했었는데, 실제로 권장되는 건지 궁금합니다.
  ```css
  .p-tag::before{
     content: '';
     display: inline-block;
     width: 15px;
     height: 15px;
     -moz-border-radius: 7.5px;
     -webkit-border-radius: 7.5px;
     border-radius: 7.5px;
     background-color: black;
  }
  ```

- SCSS를 배워서 실무에 적용하려고 하는데, 강사님은 Less 나 SCSS를 사용하시는지 궁금합니다.

#### 느낌점
- pseudo : 논문에서 자주 보이지만 가볍게 넘어갔던 용어인데, p가 묵음이라 "수도 코드", "의사 코드" 라고 사용되는 듯.
- "가상 요소"와 "가상 클래스"를 구분없이 가상클래스라고 부르고 있었는데 확실히 구분해야겠다. ( :은 가상 클래스, ::가상요소)

</details>

---


<details>
<summary> 5일차 학습</summary>

#### 인터랙티브 요소

- details 요소
  - ( 각주는 적합하지 않고 \<a>을 이용해 해쉬를 이용해 하단의 id값과 연결 )
  - open 속성을 사용하면 기본적으로 펼쳐서 사용됨
  - summary 요소와 함께 사용

- dialog
  - open 속성을 사용하면 기본적으로 펼쳐서 사용됨
  

#### 스크립팅 요소들

- type 존재하나 html5에서는 생략 가능
- src 속성을 이용해 .js 코드를 불러올 수 도 있음.
- \<style> 태그를 이용해 css코드 작성
- link 태그를 이용해 css코드도 불러올 수 있음.
```html
<link rel="stylesheet" href="css/app/css">
```

- noscript ( 크롬 디버깅 설정에는 disable javascript 뿐만 아니라 다양한 설정값이 존재 )
- canvas 

#### 유저 인터랙션 속성

- hidden ( 모든 html 요소에 가능)
- 기본적으로 포커스 가능한 요소들 (참고: https://allyjs.io/data-tables/focusable.html)
  - 폼 컨트롤 요소들           : input, button, textarea, select 등
  - href 속성을 가진 요소들     : a, area
  - controls 속성을 가진 요소들 : video, audio
- tabindex 
  - 1이상 : 탭 포커스 순서를 설정한다.
  - 0 : 포커스를 가지지 않는 요소에 부여함 ( ex \<div>)
  - -1 : 포커스를 가진 요소들을 제외함

- accesskey 속성
  - 모든 HTML 요소는 accesskey 속성을 가질 수있다. 속성 값은 키보드 단축키로 설정된다.
  - 하지만 accesskey 속성의 단축키는 브라우저와 운영체제 플랫폼에 의존하고 있어 운영체제마다 사용자 경험이 달라진다. 쉽게 말해 Windows 사용자와 Mac OSX 사용자가 사용하는 단축키는 달라진다. (iPhone과 Android 사용자 경험이 다른 것처럼)
  - [브라우저 × 운영체제 플랫폼]
  - Windows
    - Chrome  : Alt + 단축키
    - IE      : Alt + 단축키
    - Safari  : Alt + 단축키
    - Opera   : Alt + 단축키
    - Firefox : Alt + Shift + 단축키
  - Mac OSX
    - Chrome  : Control + Alt + 단축키
    - Safari  : Control + Alt + 단축키
    - Opera   : Control + Alt + 단축키
    - Firefox : Control + 단축키
  - Linux
    - Chrome  : Alt + 단축키
    - Opera   : Alt + 단축키
    - Firefox : Alt + Shift + 단축키

  [사용 예시]
  ```html        
  <button type="button" class="button is-collect" accesskey="C" onclick="collect()"> 수집</button>  
  ```


- draggable 속성
  - MDN 문서를 보니 draggable 은 Boolean이 아니라 enumerated 이기 때문에 ture, false 를 반드시 적어야 한다고 적혀있다. 열거형 이라는 것이 enum같은 것으로 추정되는데 구체적인 설명이 없어서 암기해야겠다.

#### 문서 메타데이터 요소들

- 문서의 제목과 스타일시트, 스크립트 링크 또는 선언을 포함하는 문서의 일반적인 정보(메타데이터)를 제공한다. 대부분 브라우저는 마크업에서 <head> 요소가 생략될 경우, 자동으로 <head> 요소를 생성하지만 일부는 그렇지 않다.

- 자동으로 <head> 요소를 생성하지 않는 브라우저 환경
  - Android <= 1.6
  - iPhone  <= 3.1.3
  - Opera   <= 9.27
  - Safari  <= 3.2.1.
  - Nokia 90

- title : 브라우저의 타이틀 바(Title Bar)나 페이지 탭에 보여지는 문서의 제목을 정의. 텍스트만 포함할 수 있으며 포함된 태그들은 해석되지 않음.

- 속성들을 일일이 설명하지 않고 아래의 예시 코드로 표현함
  ```html
  <!DOCTYPE html>
  <html lang="ko-KR">
    <head>
      <meta charset="UTF-8">
      <title>HTML 메타데이터(Metadata) 요소들</title>
      <meta name="application name" content="어플리케이션 이름 정의">
      <!--웹 페이지에서 실행중인 웹 애플리케이션 이름 정의. 
      간단한 웹 페이지는 application-name 메타를 정의해서는 안됨. -->
      <meta name="description" content="웹페이지 내용을 요약해서 기술">
      <meta name="keywords" content="웹페이지의 주요 키워드를 콤마(,) 로 구분하여 작성.">
      <meta name="author" content="웹페이지 제작자">
      <meta name="robots" content="index">
      <meta name="viewport" content="width=device-width,  initial-scale=2">
    </head>
    <body>
    </body>
  </html>
  ```
- \<base> 요소를 이용하여 href 의 base주소를 설정가능하다.
- \<link> 요소를 이용해 css을 가져올 때 title을 부여하여 스타일을 변경할 수도 있는데 크롬에서는 불가능하다.




  
#### 질문
- hidden 속성과 css 의 "display : none" 시각적 효과는 비슷한데 어떤 차이가 있는지 궁금합니다.


#### 느낌점
- meta태그에서 "application-name" 은 간단한 웹 페에지는 적용할 수없다고 하였는데, 여기저기 찾아보니 gmail.com 에 application-name 이 적용되어 있다. 

- \<style>에서 scoped 는 대부분의 브라우저에서 지원되지 않는 기능이라고 설명들었다. 다만 vue.js를 주로 쓰는 나에게는 매우 친숙한 속성값이다.

- details, summary의 경우는 TIL 과제를 하며 다른사람들의 과제를 참고하다가 다른 분들이 일자별로 details 태그를 이용하며 분리하는 것을 보고 따라하며 배웠다.

- 항상 다이얼로그는 div요소를  z-index, display: none, position: absolue 등의 css 와 js를 이용해 만들었는데, \<dialog> 태그가 있었다니 다음에 사용해봐야겠다.

- 논리적인 흐름이 중요하다. markup의 순서 즉 먼저 등장하는 것이 우선시된다. 그러므로 img요소의 tabindex 요소를 0이 아닌 양수로 주는 것은 권장되지 않는다.

- 접근성 관점에서 웹페이지 내 "드래그앤드드롭"을 구현하면 마우스없이 키보드로도 가능하게 해야한다.

</details>

---

<details>
<summary> 4일차 학습</summary>

#### 테이블 요소

- table은 항상 제목(caption) 을 가진다. ( MDN 사이트을 보니 선택인듯)
- table, caption, column, th, dh, tr, colspan,
- 전맹 시각자의 경우 table은 매우 이해하기 어렵기 때문에 구조화를 잘해야 한다.
- table 의 border 속성은 표현이라 사용이 권장되지 않는다. (가능한 표현은 css을 통해서 해야한다.)
- 가장 좋은 테이블 디자인은 단순해서 이해하기 쉽게 만드는 것이며 테이블 내 테이블을 중첩해서는 안된다. 
- 테이블을 레이아웃(배치) 목적으로 사용해서는 안된다. 
- 테이블 내용이 복잡하여 설명이 필요하다면 아래 두가지 방법 중 하나를 선택 해야한다. 
  - 1. aria-describedby 속성으로 표에 대한 자세한 설명단락의 id와 연결시킨다.
    ```html
    <p id="compare-shoes-table">테이블 내용에 대한 설명 블라블라~</p>
    <table aria-describedby='compare-shoes-table'>
      <caption>성인 남성 운동화 사이즈표</caption>
      <tr>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      <tr></tr>
      <tr></tr>
    </table>
    ```
  - 2. \<figure> 요소에 aria-labelledby 속성을 사용해 제목(caption과 연결시킨다.)
  
    ```html
    <figure aria-labelledby="compare-shoes-table">
    <p >테이블 내용에 대한 설명 블라블라~</p>
    <table>
      <caption id="compare-shoes-table">성인 남성 운동화 사이즈표</caption>
      <tr>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      <tr></tr>
      <tr></tr>
    </table>
    </figure>
    ```  
    
- th 요소
  - 테이블 셀 제목(header cell in a table)으로 행(tr) 내부에 포함되어야 한다.
  - 속성
    - scope: 행(row) 또는 열(col), 행그룹(rowgroup), 열그룹(colgroup)의 제목임을 명시
    - abbr: 제목이 길어 축약(Abbreviation)이 필요할 때 사용
    - colspan: 열(column)을 그룹 지을 때 사용
    - rowspan: 행(row)을 그룹 지을 때 사용 (보통 1행 1열)

- td 요소
  - 테이블 셀 내용(data cell in a table)으로 행(tr) 내부에 포함되어야 한다.
  - 속성
    - colspan: 열(column)을 그룹 지을 때 사용
    - rowspan: 행(row)을 그룹 지을 때 사용
    - headers: 셀 제목을 하나 이상 연결하여 읽기 용이하도록 구성할 때 사용, 스크린 리더가 순서대로 읽음.
    
- thead 요소
  - 테이블 행 블록(row block) 내에 제목 열 그룹(column headers)으로 구성할 경우 사용한다. 
  - 선택적(option)으로 사용한다. (필수 아님)

- tbody 요소
  - 행 블록 내에 테이블 데이터로 구성할 때 사용한다. 
  - 선택적(option)으로 사용한다. (필수 아님)
  - 기본적으로 브라우저가 알아서 묶어만들어주기도 함

- tfoot 요소
  - 행 블록 내에 열 요약(column summaries)로 구성할 때 사용한다. 
  - 선택적(option)으로 사용한다. (필수 아님)

- col 요소
  - 테이블 열(column)을 하나 이상 묶고자 할 때 사용한다.
  - 일반적으로 colgroup 요소 내부에 포함시킨다.
  - 선택적(option)으로 사용한다. (필수 아님)
  - 속성
    - span: 열 묶음 개수 설정

- colgroup 요소
  - 테이블 열(column) 그룹을 만들고자 할 때 사용한다.
  - 내부에 col 요소를 포함하거나, 포함하지 않을 수 있다.
  - 선택적(option)으로 사용한다. (필수 아님)
  - 속성
    - span: colgroup 요소가 col을 포함하지 않을 경우, 열 묶음 개수 설정    

#### form , input , button 등의 폼 요소

```html
<form action="https://formspree.io/your@email.com" method="POST">
  <label>이름 <input type='text' name="user_name"  placeholder="이민주" maxlength='4'></label>
</form>
``` 
- name : 서버에 값을 전송할 때 사용됨
- label 태그의 for 속성 유무
  - for 속성을 사용하지 않으면 \<label>태그 내부에 \<input> 사용
  - for 속성을 사용하면 \<label> 과 \<input>을 분리 가능 => 다만 이때에는 반드시 label태그의 for 속성과 input 태그의 id 속성이 동일해야함
    ```html
    <form action="https://formspree.io/your@email.com" method="POST">
      <label for='_user_name'>이름 </label>
      <input type='text' _id="_user_name" name="user_name"  placeholder="이민주" maxlength='4'>
    </form>
    ```

- input
  - 속성
    - name
    - placeholder
    - value : 실제 값
    - readonly : 읽기 전용
    - required : 필수 입력 사항
    - disabled
    - minlength
    - maxlength
    - list
  - type
    - text
    - password
    - checkbox
    - radio : label 로 묶으면 레이블을 클릭해도 선택이 된다. default의 의미로 checked 속성 추가가능하며 반드시 name값이 동일해야 한다.
    - file : File 전송시에 from 요소의 enctype="multipart-formdata" 을 추가 및 method는 POST 설정.
    - submit : button 태그를 사용하지 않고 input 태그로 사용. 이때 value 속성으로 text 입력
    - button 
    - image : image 타입을 이용해 이미지 버튼을 만들 수 있음.
    - reset
    - hidden : 사용자에게 보여지지 않고 데이터 전송
    - search : x 표시 가능
    - url : datalist 요소( option 태그도 )를 이용하여 list 속성을 통해 listing 가능
    ```html
    <p>
      <label> 이동할 웹주소<input list="url_ex" type="url" name="user_url" ></label>
      <datalist>
        <option value="http://naver1.com"></option>
        <option value="http://naver2.com"></option>
        <option value="http://naver3.com"></option>
        <option value="http://naver4.com"></option>
      </datalist>
    </p>
    ```
    - tel : 전화번호도 datalist 사용가능
    - email
    - date
    - month
    - week
    - time
    - datetime-local
    - number : min, max, step(한번 올릴 때 마다 단위), value로 초기값 설정 가능
    - range : min, max, step(한번 올릴 때 마다 단위), value로 초기값 설정 가능
    - color : value 을 통해 초기값 설정 가능

- datalist
  - 데이터 목록 요소 컨테이너 컨트롤.
  - 내부에 \<option> 요소를 사용해 항목을 만든다.

- button
  - 버튼 폼 컨트롤로 사용자의 인터랙션을 받아 액션을 트리깅(방아쇠) 처리함.
  - contents 값으로 "생성 버튼" 이런식으로 넣으면 안됨 => 스크린리더가 버튼태그를 버튼으로 읽으므로 "생성 버튼 버튼" 으로 읽음
  - type
    - submit
    - button : 일반 버튼
    - reset : 초기화
    
  ```html
  <button type="submit"></button>
  ```



- select, option, optgroup
  - 드롭 다운 메뉴(옵션을 선택 할 수 있는) 컨트롤을 말함. 내부에 \<option> 요소를 포함하여 사용자에게 선택할 수 있도록 한다. \<option>을 묶어 그룹으로 만들고자 한다면 \<optgroup> 요소를 사용하고, label 속성을 사용해 그룹 이름을 설정한다.
  
  - select
  - 속성
    - name
    - multiple
    - disabled
    - required
    - size

  - option
    - \<select>, \<datalist>, \<optgroup> 내부에 포함 가능한 컨트롤로 항목을 만드는데 사용됨.
    - 속성
      - value
      - selected
      - label
      - disabled
      
  - optgroup
    - \<option> 컨트를을 그룹지을 때 사용됨.
    - 속성
      - disabled
      - label
  ```html      
  <p>
    <label for="user_hobby">취미</label>
    <select name="user_hobby" id="user_hobby" required>
      <option value="0">없음</option>
      <optgroup label="구기종목">
        <option value="1" selected>축구</option>
        <option value="2" label="basketball" disabled>농구</option>
      </optgroup>
      <optgroup label="문화생활" disabled>
        <option value="3">독서</option>
        <option value="3">영화관람</option>
      </optgroup>
    </select>
  </p>
  ```

- textarea
  - 멀티라인 일반 텍스트 편집 컨트롤을 말한다.
  - type
    - name
    - placeholder
    - rows : 높이
    - cols : 글자의 개수
    - readonly
    - required
    - disabled
    - minlength
    - maxlength
  - css
    - resize : none 속성으로 UI 변경할 수 없도록 만듬.

  ```html
  <div>
    <label for="user_comments">코멘트</label>
    <p>
      <textarea name="user_comments" id="user_comments" cols="24" rows="5">남기고 싶은 말을 작성해주세요<textarea>
    </p>
  </div>
  ```

- fieldset
  - 하나 이상의 폼 컨트롤을 그룹화 하는데 사용됨.
  - 속성    
    - name
    - disabled
- legend
  - \<fieldset> 컨트롤의 레이블(이름)을 설정하는 컨트롤.

  ```html
  <fieldset name="user_acount">
    <legend>사용자 계정</legend>
  </fieldset>
  ```

- output
  - 계산된 결과를 출력하는 컨트롤.
  - 속성
    - name
    - for
      
  ```html        
  <form oninput="result_sum.value = parseInt(n1.value + n2.value, 10)">
    <p>
      <input type="number" name="n1" value="4"> +
      <input type="number" name="n2" value="10"> =
      <output name="result_sum">14</output>
    </p>
  </form>
  ```
- progress
  - 작업의 완료 진행 상황을 표시하는데 사용되는 컨트롤.
  - 속성
    - value
    - max
  

  ```html
  <progress value="10" max="100">10%</progress> 
  <!-- 아직 10% 라는 content가 반영 안됨 -->
  ```
- meter
  - 알려진 범위 내에서의 스칼라 측정 또는 분포 비율을 나타내는 컨트롤. (게이지(gauge)라고도 불림)
      디스크 사용 현황, 쿼리 결과의 관련성, 특정 후보에 대한 투표율 등이 해당됨.
  - 속성
    - value
    - min
    - max
    - low
    - high
    - optimum

  ```html
  <meter value="20" min="5" max="40">20</meter>
  <!-- 아직 20 이라는 content가 반영 안됨 -->
  ```
  
#### 질문
없음

#### 느낌점
form과 관련된 많은 타입들을 배웠다.
또한 가장 좋은 테이블 디자인은 단순해서 이해하기 쉬운 디자인이라는 것 ! 그리고 테이블 내 테이블을 중첩해서는 안된다는 말을 기억해야겠다.

</details>

---


<details>
<summary> 3일차 학습</summary>

#### 컨테이너 요소

- 적절한 시맨틱 요소가 없을때만 div, span 사용
- div
  - div : division 의 약자
  - block 컨테이너 (html5 에서는 flow)
  - block 요소( h1~6, p, blockquote, section )

- span
  - 인라인 요소( a, strong, em, b, i )
  - 인라인 요소는 블록요소를 감쌀 수 없다.



#### 텍스트 레벨 요소


- 아래 첨자 : \<sub>  subscript text 
- 위 첨자 : \<sup>  superscript text ( ex) 각주 )
- 텍스트 하이라이트 : \<mark>
- 축약어 : \<abbr> Abbreviation
- 취소선 : \<s> strikethrough 
- 시간 /날짜 요소 : \<time> 기계가 이애할 수 잇는 형태로 날짜나 시간을 나타냄


#### 그룹핑 요소

- address 
  - 조직의 정보

```html
<address>
  서울특별시 강남구 삼성로 648 SM ENTERTAINMENT
  Communication Center 대표전화 <a href="tel:+82262409800">02 6240 9800</a>   
  대표 : 한세민, 남소영 사업자번호 <a href="https://goo.gl/XqFuCC">114 81 63109</a> 
  <small>Copyright©2013 SM ENTERTAINMENT Co., Ltd. ©All rights reserved.</small>
</address>
```

- pre ( preserved 의 약자이며 code 의 경우 \<code> 이용) 
  - 이메일, 빈줄이 표시된 단락, 아스키코드
  - 컴퓨터 코드, 출력, 키보드 블록을 나타내기 위해 pre 요소는 code, samp, kbd 요소와 함께 사용 가능

```html
<pre>
____  ∧ ∧
   |＼ /(´～`)＼&lt변화구
   |　|￣￣￣￣￣|
   |　|＝みかん＝|
 ＼|＿＿＿＿＿|
</pre>
<pre>
<p>다음은 패널(Panel) 생성자 함수(Constructor Function) 입니다.</p>
function Panel(element, canClose, closeHandler) {
  this.element = element;
  this.canClose = canClose;
  this.closeHandler = function () { if (closeHandler) closeHandler() };
}
</pre>
```




#### 임베디드 요소

- embed, object, param 는 자주 사용되지 않음

- picture
  - source, img 모두 가능하다.
  - img를 포함하는 컨테이너 요소이며 모던 브라우저에서는 다양한 디바이스에 대응하기 위해 source 요소를 사용가능하다.

```html
<picture>
  <source srcset='media/image1~~~' type='image/png' media="(min-width:900px)">
  <source srcset='media/image2~~~' type='image/png' media="(min-width:600px)">
  <img src='media/image3~~~' alt='웃는 고양이'>
</picture>
```

- video
  - 속성으로 src, poster, preload, controls, autoplay, loop, muted 존재 
```html
<video
  src='media/video/~~'
  poster='media/~~.png'
  controls autoplay loop muted>
  <p>
    HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹브라우저를 사용중입니다.
    <a href='http://outdatedbrowser.com/ko'>최신형 브라우저로 업데이트</a> 하세요.
  </p>
</video>
```

- Audio
  - control 속성이 없으면 audio control이 기본적으로 보이지 않음.
  - 아래 코드는 figcaption 내부에 audio태그를 넣고 width를 동일하게 하여 디자인된 화면을 구성 (control의 가로폭이 300px )
  - https://caniuse.com/#search=mp3 ( 결론적으로 mp3, mp4 를 사용하면 되므로 더이상 내부에 source 를 이용해 다양한 포멧을 사용할 필요 없음.)

```html
<figure>
  <img src='media/image/~~~.png alt='비행기' width='300' height='300'>
  <figcaption>
    <audio src='media/~~~.mp3' controls>
      <p>
        HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹브라우저를 사용중입니다.
        <a href='http://outdatedbrowser.com/ko'>최신형 브라우저로 업데이트</a>  하세요.
      </p>
    </audio>
  </figcaption>
</figure>
```

- track
  - video, audio 안에서  사용
  - 다국어도 사용 가능 ( default 가능)
  - vtt = video text track 웹표준 자막 포멧

```html
<video src='media/video/~~' controls >
  <track kind='subtitles' src='~~.ko.vtt' srclang='ko' label='한국어'  default>
  <track kind='subtitles' src='~~.ko.vtt' srclang='en' label='영어'>
  <track kind='subtitles' src='~~.ko.vtt' srclang='ja' label='일본어'>
    
</video>
```

- iframe
  - src             - 프레임 소스 설정
  - width           - 프레임 너비 설정
  - height          - 프레임 높이 설정
  - allowfullscreen - 프레임 전체화면 설정
  - frameborder='0' - 프레임 테두리 설정
  - allow - 허용 시켜줄 대상 ( allow="autoplay; encrypted-media" )
  - 구글 맵, 네이버맵 등 시간이 날때 직접 해봐야겠다.

- map 요소
  - 이미지 맵 좌표 생성: https://www.image-map.net/
  - 이미지 맵(클릭 가능한 링크 영역)을 정의하기 위해 \<area>와 함께 사용됨.

- area 요소
  - 이미지의 핫스팟 지역 정의, 하이퍼링크 설정. 내부에서만 사용 가능.
  - shape    - 핫스팟 모양 설정
  - coords   - 모양의 좌표 값 설정
  - href     - 하이퍼링크 주소 설정
  - target   - 새 창(탭) 열림 설정
  - alt      - 대체 텍스트 설정
  - hreflang - 연결된 페이지의 언어 속성 설정
  - download - canvas 데이터 다운로드 설정

```html
<img src="products-map.jpg" alt="제품 모음" usemap="#products-map">
<map name="products-map">
  <area
    shape="circle"
    coords="200,250,25"
    hreflang="en-GB"
    href="another.html"
    alt="Another Page"
    target="_blank">
</map>
```


#### 질문
없습니다. 

#### 느낌점
- 오늘은 매우 관심있는 주제가 많았다.
- 예전의 보안이슈로 iframe 이야기를 많이 들었는데 제대로 다시 공부해봐야겠다.
동영상 업로드 기능이나 실시간 스트리밍 서비스 관련하여 video 태그를 좀더 살펴보고 싶다. 
- map 요소라는 것이 있는지 처음 알았다. 비슷한 기능을 구현하기 위해 자바스크립트와 - - div를 이용해서 구현했었는데, 앞으로는 map요소를 사용해야겠다.
항상 느끼는 canvas에 비해 svg의 가장 큰 장점은 css, javascript를 적용 가능하다는 점이다.
</details>

---

<details>
<summary> 2일차 학습 </summary>

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
  -설명 목록(dl : description List) =  용어(dt : term) + 해당 용어에 설명내용(dd : description)
태그 속성에 값에 넣는 문자는 entitycode 로 할 필요 없음
img에 title 속성을 통하여 툴팁 가능

- 인용과 줄바꿈
인용 : \<q\> quotation ( cite 속성 사용 가능)
인용단락(긴 인용문) : \<blockquote\> blockquote
출처 : \<cite\> citation
\<br\>은 linebreak 용도로 사용하고 두번사용해서는 안됨.
 

- 어휘 요소들
  - 아래 두가지를 구분해야 함 (즉 bold 가 의미적으로 강조가 아니다.)
  - 1)강조 : sematic
  - 2)표현적인 목적 : Non sematic
  - \<strong\> 중요성, 심각성 , 긴급성


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
  - main 요소는 섹션요소가 아니며, main은 반드시 1개만 보여져야 하므로, hidden 속성을 이용해야 한다. 
```html
  <main> </main>
  <main hidden> </main> 
```
  - <참고>
  - article, section, aside, nav 는 main요소를 자식으로 포함할 수 없다. 
  - 반대로 main요소는 섹션(article, section, aside, nav)요소들을 포함할 수 있다. 
  - main 내부에는 header, footer 요소를 직접적으로 포함하지 않는다. (섹션 내부에  - footer와, header을 넣는다.)
  - body 안에는 직접적으로 header, footer 요소를 직접적으로 포함 가능.



#### 질문
1. 시멘틱 태그가 너무 많아 실제로 적용시키기 쉽지 않을 것 같습니다. 시멘틱 태그도 꼼꼼히 작성하는 것을 웹 표준, 웹 접근성(?) "준수"라고 표현하는 것 같은데 실제 웹사이트가 웹 표준이나 접근성이 지켜지지 않을 경우 어떤 불이익이 있는지 궁금합니다. 

#### 느낌점
과제가 많이 늦었습니다!

</details>

---
<details>
<summary> 1일차 학습 </summary>

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
- 나머지 영상도 간단히 살펴보았는데, 내가 모르는 태그나 매우 많았다. 알고 안쓰는 것과 몰라서 안쓰는 것은 큰 차이니 열공!!
- 항상 영어문서만 봤었는데, mdn한글 문서도 보니 번역이 잘되어 있네, 기계번역이 아닌것 같다.

</details>

---