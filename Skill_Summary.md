# STARBUCKS 프로젝트에 사용된 기술 정리

## Ⅰ. index.html

### **_1. reset-css 설정 (P1.Ch10.01)_**

- 브라우저에서 제공하는 기본 스타일을 초기화 (jsDelivr reset css)

### **_2. 오픈그래프 설정 (P1.Ch10.02)_**

- 웹페이지가 SNS로 공유될 때 우선적으로 활용되는 정보
- <meta property="og:type" content="website"/>
- og property 종류 = type, site_name, title, description, image, url
- <meta property="twitter:type" content="website"/>
- twitter property 종류 = card, site, title, description, image, url

### **_3. 구글폰트 설정 (P1.Ch10.03)_**

- 구글폰트 → 폰트검색 → 폰트굵기 선택 → <link>방식으로 index.html에 복붙
  (main.css의 link태그보다 윗줄에 작성)

### **_4. Material Icons 설정 (P1.Ch10.04)_**

- <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet"> index.html에 복붙
  (구글폰트 link태그 아래에 작성)
- <div class="material-icons">아이콘이름</div> 복붙
  (원하는 위치에 적용)
- main.css에서 .material-icons 선택자 추가 후 옵션 부여
  <br>
  <br>

## Ⅱ. main.css

### **_1. Common 속성 설정_**

- body, img, a, .btn 등 공통으로 적용되는 태그에 기본 설정값을 재설정 해주는 작업
- body { color: #333; font-size: 16px; font-weight: 400; ...}
- img { display: block; }, a { text-decoration: none; } 등
- .btn { width,padding,border,border-radius,color,font-size,font-weight,text-align,cursor,box-sizing,display,transition }
- input { outline:none; border: 1px solid #ccc; border-radius: 5px; box-sizing: border- box; background-color: #fff; color: #777; },

### **_2. inner 선택자 설정 (P1.Ch10.05)_**

- 웹페이지의 내용이 표기 될 공간의 너비를 설정 및 가운데로 몰아주는 역할
- Common 속성 부분에 작성
- width 설정 → margin: 0 auto; → position:relative

### **_3. 요소의 가운데 배치_**

- 요소의 부모요소에 position:relative 속성 부여
- 요소에 width (혹은 height) 값을 부여
- 요소에 position:absolute 속성 부여 후 left,right (혹은 top,bottom) 속성에 0값을 부여
- 요소에 margin 속성에 0 auto (혹은 auto 0) 값을 부여

### **_4. a태그의 javascript:void(0)_**

- a태그의 링크 기능을 막음
- 해시태그(#)보다 void를 사용하는것을 더욱 추천

### **_5. 요소 사이에 구분선 넣기_**

- ::before 가상요소 선택자 를 사용
- 선택자::before {
  content: "";
  width: 1px;
  height: 12px;
  background-color: #333;
  position: absolute; (부모요소에 position:relative 부여)
  top: 0;
  bottom: 0;
  left: 1px;
  }
  <br>
  <br>

## Ⅲ. main.js

### **_1. JS에서 scroll값 구하기 (loadsh cdn) + JS에서 애니메이션 구현하기 (Gsap)_**

#### a. lodash cdn으로 scroll값 구하기

- **lodash library로 scroll시 빠르게 반복되는 작업들로 인한 과부하를 컨트롤 할 수 있음**
- lodash cdn에서 lodash.min.js을 index.html의 main.js script태그 위에 복붙
- window.addEventListener('scroll', \_.throttle(function () {
  if (window.scrollY > 500){
  스크롤 값이 500보다 클때 기능(gsap 구현)
  } else {
  스크롤 값이 500보다 작을때 기능(gsap 구현)
  }
  }),300);
  <!--_.throttle(함수,시간)-->

#### b. Gsap으로 js에서 애니메이션 구현하기

- **gsap library로 js에서 애니메이션을 구현할 수 있음**
- gsap cdn에서 gsap.min.js를 index.html의 main.js script태그 위에 복붙
- gsap.to(badgeEl, .6, {
  opacity: 0,
  display: 'none',
  });
- gsap.to(badgeEl, .6, {
  opacity: 1,
  display: 'block',
  });
    <!-- gsap.to(요소,지속시간,함수) -->
  **_ 관련 내용은 fastcampus 프론트엔드 개발 초격차 패키지 Online. P1.Ch10.11~12에서 확인 가능_**

### **_2. JS에서 애니메이션을 순차적으로 구현하기 (Gsap)_**

- const fadeEls = document.querySelectorAll('.visual .fade-in'); //요소를 유사배열객체로 선언
- fadeEls.forEach(function (fadeIn, index) {
  gsap.to(fadeIn, 1, {
  opacity: 1,
  delay: (index + 1) \* .7, // 0.7, 1.4, 2.1, ...
  });
  });
  **_ 관련 내용은 fastcampus 프론트엔드 개발 초격차 패키지 Online. P1.Ch10.15에서 확인 가능_**
  <br>
  <br>

## Ⅳ. youtube.js
