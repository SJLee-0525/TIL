**CSS 프론트엔드 프레임워크**

→ 미리 만들어진 다양한 디자인 요소들을 제공하여 웹 사이트를 빠르고 쉽게 개발할 수 있도록 함

```html
HTML: 콘텐츠의 구조와 의미

CSS: 레이아웃과 디자인
```

### 사용 방법

1. https://getbootstrap.com 접속
2. Docs → Introduction → Quick Start
3. Include Bootstrap’s CSS and JS 코드 확인 및 가져오기

![image.png](images/bt1.png)

### CDN (Content Delivery Network)

지리적 제약 없이 빠르고 안전하게 콘텐츠를 전송할 수 있는 전송 기술

- 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간 최소화
- 지리적으로 사용자와 가까운 CDN 서버에 콘텐츠를 저장해서 사용자에게 전달

**Bootstrap CDN**

1. Bootstrap 홈페이지 - Download - ‘Compiled CSS and JS’ 다운로드
2. CDN을 통해 가져오는 bootstrap css와 js 파일을 확인
3. bootstrap.css, bootstrap.js 파일 참고
    
    → 온라인 CDN 서버에 업로드 된 css 및 js 파일을 불러와서 사용하는 것
    

### 사용하는 이유

- 가장 많이 사용되는 CSS 프레임 워크
- 사전에 디자인된 다양한 컴포넌트 및 기능
    - 빠른 개발과 유지보수
- 손쉬운 반응형 웹 디자인 구현
- 커스터마이징 용이
- 크로스 브라우징(Cross browsing) 지원
    - 모든 주요 브라우저에서 작동하도록 설계되어 있음

### 사용법

**Bootstrap 기본 사용법**

```html
<p class="mt-5">Hello, wordld!</p> 

mt-5
{property}{sides}-{size}
```

**Bootstrap에서 클래스 이름으로 Spacing을 표현하는 방법**

![image.png](images/bt2.png)

```html
- t , b , s , e ,x , y  의 의미
       - t : top을 의미 
       - b : bottom을 의미
       - s : left을 의미
       - e : right을 의미
       - x : x축 -> left , right을 의미
       - y : y축 -> top , bottom을 의미

- 0, 1, 2, 3, 4, 5, auto  의 의미
       - 0 : 0
       - 1 : .25rem( font-size가 16px이면, 4px) 크기
       - 2 : .5rem( font-size가 16px이면, 8px) 크기
       - 3 : 1rem( font-size가 16px이면, 16px) 크기 << 기본 폰트 사이즈
       - 4 : 1.5rem( font-size가 16px이면, 24px) 크기
       - 5 : 3rem( font-size가 16px이면, 48px) 크기
       - auto : margin의 자동으로 세팅

- n1, n2, n3, n4, n5 의 의미 
   - n : negative을 의미
       - n1 : -.25rem( font-size가 16px이면, -4px) 크기
       - n2 : -.5rem( font-size가 16px이면, -8px) 크기
       - n3 : -1rem( font-size가 16px이면, -16px) 크기
       - n4 : -1.5rem( font-size가 16px이면, -24px) 크기
       - n5 : -3rem( font-size가 16px이면, -48px) 크기
출처: https://minaminaworld.tistory.com/136 [미나미 블로그:티스토리]
```

**Bootstrap에는 특정한 규칙이 있는 클래스 이름으로 스타일 및 레이아웃이 미리 작성되어 있음**

**Bootstrap 적용 전 / 후 비교**

![image.png](images/bt3.png)

### Reset CSS

모든 HTML 요소 스타일을 일관된 기준으로 재설정하는 간결하고 압축된 규칙 세트

→ HTML Element, Table, List 등의 요소들에 일관성 있게 스타일을 적용시키는 기본 단계

**Reset CSS 사용 배경**

- 모든 브라우저는 각자의 ‘user agent stylesheet’를 가지고 있음
    - 웹사이트를 보다 읽기 편하게 하기 위해
- 문제는 이 설정이 브라우저마다 상이하다는 것
- 모든 브라우저에서 웹사이트를 동일하게  보이게 만들어야 하는 개발자들에겐 골치 아픈 일

→ 모두 똑같은 스타일 상태로 만들고 스타일 개발을 시작하자!

**User-agent stylesheets**

- 모든 문서에 기본 스타일을 제공하는 기본 스타일 시트

![image.png](images/bt4.png)

**Normalize CSS**

- Reset CSS 방법 중 대표적인 방법
- 웹 표준 기준으로 브라우저 중 하나가 불일치한다면 차이가 있는 브라우저를 수정하는 방법
    - 경우에 따라 IE또는 Edge 브라우저는 표준에 따라 수정할 수 없는 경우도 있는데,
    이 경우 IE 또는 Edge의 스타일을 나머지 브라우저에 적용시킴

## Bootstrap 활용

### Typography (제목, 본문 텍스트, 목록 등)

- **Display headings**
    
    기존 Heading보다 더 눈에 띄는 제목이 필요할 경우 (더 크고 약간 다른 스타일)
    
    ```html
    <h1 class="display-1">Display 1</h1>
    <h1 class="display-2">Display 2</h1>
    <h1 class="display-3">Display 3</h1>
    <h1 class="display-4">Display 4</h1>
    <h1 class="display-5">Display 5</h1>
    <h1 class="display-6">Display 6</h1>
    ```
    

- **Inline text elements**
    
    HTML inline 요소에 대한 스타일 
    
    ![image.png](images/bt5.png)
    

- **List**
    
    HTML list 요소에 대한 스타일
    
    ```html
    <ul class="list-unstyled">
      <li>This is a list.</li>
      <li>It appears completely unstyled.</li>
      <li>Structurally, it's still a list.</li>
      <li>However, this style only applies to immediate child elements.</li>
      <li>Nested lists:
        <ul>
          <li>are unaffected by this style</li>
          <li>will still show a bullet</li>
          <li>and have appropriate left margin</li>
        </ul>
      </li>
      <li>This may still come in handy in some situations.</li>
    </ul>
    ```
    

### Colors

- **Bootstrap Color system**
    
    부트 스트랩이 지정하고 제공하는 색상 시스템
    

- **Text colors**

```html
  <!-- text colors -->

  <p class="text-primary">.text-primary</p>
  <p class="text-primary-emphasis">.text-primary-emphasis</p>
  <p class="text-secondary">.text-secondary</p>
  <p class="text-secondary-emphasis">.text-secondary-emphasis</p>
  <p class="text-success">.text-success</p>
  <p class="text-success-emphasis">.text-success-emphasis</p>
  <p class="text-danger">.text-danger</p>
  <p class="text-danger-emphasis">.text-danger-emphasis</p>
  <p class="text-warning bg-dark">.text-warning</p>
  <p class="text-warning-emphasis">.text-warning-emphasis</p>
  <p class="text-info bg-dark">.text-info</p>
  <p class="text-info-emphasis">.text-info-emphasis</p>
  <p class="text-light bg-dark">.text-light</p>
  <p class="text-light-emphasis">.text-light-emphasis</p>
  <p class="text-dark bg-white">.text-dark</p>
  <p class="text-dark-emphasis">.text-dark-emphasis</p>
```

- **Background colors**

```html
  <!-- background colors -->

  <div class="p-3 mb-2 bg-primary text-white">.bg-primary</div>
  <div class="p-3 mb-2 bg-primary-subtle text-primary-emphasis">.bg-primary-subtle</div>
  <div class="p-3 mb-2 bg-secondary text-white">.bg-secondary</div>
  <div class="p-3 mb-2 bg-secondary-subtle text-secondary-emphasis">.bg-secondary-subtle</div>
  <div class="p-3 mb-2 bg-success text-white">.bg-success</div>
  <div class="p-3 mb-2 bg-success-subtle text-success-emphasis">.bg-success-subtle</div>
  <div class="p-3 mb-2 bg-danger text-white">.bg-danger</div>
  <div class="p-3 mb-2 bg-danger-subtle text-danger-emphasis">.bg-danger-subtle</div>
  <div class="p-3 mb-2 bg-warning text-dark">.bg-warning</div>
  <div class="p-3 mb-2 bg-warning-subtle text-warning-emphasis">.bg-warning-subtle</div>
  <div class="p-3 mb-2 bg-info text-dark">.bg-info</div>
  <div class="p-3 mb-2 bg-info-subtle text-info-emphasis">.bg-info-subtle</div>
  <div class="p-3 mb-2 bg-light text-dark">.bg-light</div>
  <div class="p-3 mb-2 bg-light-subtle text-light-emphasis">.bg-light-subtle</div>
  <div class="p-3 mb-2 bg-dark text-white">.bg-dark</div>
  <div class="p-3 mb-2 bg-dark-subtle text-dark-emphasis">.bg-dark-subtle</div>
  <div class="p-3 mb-2 bg-body-secondary">.bg-body-secondary</div>
  <div class="p-3 mb-2 bg-body-tertiary">.bg-body-tertiary</div>
  <div class="p-3 mb-2 bg-body text-body">.bg-body</div>
  <div class="p-3 mb-2 bg-black text-white">.bg-black</div>
  <div class="p-3 mb-2 bg-white text-dark">.bg-white</div>
  <div class="p-3 mb-2 bg-transparent text-body">.bg-transparent</div>
```

- **Bootstrap 실습**
    
    ![image.png](images/bt6.png)
    
    ```html
    <!DOCTYPE html>
    <html lang="en">
    
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
      <style>
        .box {
          width: 200px;
          height: 200px;
        }
      </style>
    </head>
    
    <body>
      <div class="box border border-5 border-dark bg-info"></div>
    
      <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
        crossorigin="anonymous"></script>
    </body>
    
    </html>
    
    ```
    

### Bootstrap Component

Bootstrap에서 제공하는 UI 관련 요소

- **Alert**

```html
<!-- alerts -->
<div class="alert alert-primary" role="alert">
  A simple primary alert—check it out!
</div>
<div class="alert alert-secondary" role="alert">
  A simple secondary alert—check it out!
</div>
<div class="alert alert-success" role="alert">
  A simple success alert—check it out!
</div>
<div class="alert alert-danger" role="alert">
  A simple danger alert—check it out!
</div>
<div class="alert alert-warning" role="alert">
  A simple warning alert—check it out!
</div>
<div class="alert alert-info" role="alert">
  A simple info alert—check it out!
</div>
<div class="alert alert-light" role="alert">
  A simple light alert—check it out!
</div>
<div class="alert alert-dark" role="alert">
  A simple dark alert—check it out!
</div>
```

- **Badges**

```html
<h1>
  <button type="button" class="btn btn-primary position-relative">
    Inbox
    <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
      99+
      <span class="visually-hidden">unread messages</span>
    </span>
  </button>
</h1>
```

- **Buttons**

```html
<p class="d-inline-flex gap-1">
  <button type="button" class="btn" data-bs-toggle="button">Toggle button</button>
  <button type="button" class="btn active" data-bs-toggle="button" aria-pressed="true">Active toggle button</button>
  <button type="button" class="btn" disabled data-bs-toggle="button">Disabled toggle button</button>
</p>
<p class="d-inline-flex gap-1">
  <button type="button" class="btn btn-primary" data-bs-toggle="button">Toggle button</button>
  <button type="button" class="btn btn-primary active" data-bs-toggle="button" aria-pressed="true">Active toggle button</button>
  <button type="button" class="btn btn-primary" disabled data-bs-toggle="button">Disabled toggle button</button>
</p>
```

- **Cards**

```html
<!-- Cards -->
<div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

- **Navbar**

```html
<!-- navbar -->
<nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Features</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Pricing</a>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" aria-disabled="true">Disabled</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
```

## Semantic Web

웹 데이터를 의미론적으로 구조화된 형태로 표현하는 방식

### Semantic in HTML

**HTML 요소가 의미를 가진다는 것**

```html
<p style="font-size: 30px;">Heading</p>
# 단순히 제목처럼 보이게 큰 글자로 만드는 것

<h1>Heading</h1>
# '페이지 내 최상위 제목'이라는 의미를 제공하는 요소 h1
	- 브라우저에 의해 스타일이 지정됨
```

**HTML Semantic Element**

기본적인 모양과 기능 이외에 의미를 가지는 HTML 요소

→ 검색엔진 및 개발자가 웹 페이지 콘텐츠를 이해하기 쉽도록

**대표적인 Semantic Element**

아래의 요소들은 `div` 와 완벽하게 동일한 기능을 수행함 

- `header`
- `nav`
- `main`
- `article`
- `section`
- `aside`
- `footer`

![image.png](images/bt7.png)

### Semantic in CSS

**CSS 방법론**

CSS를 효율적이고 유지 보수가 용이하게 작성하기 위한 일련의 가이드라인

### OOCSS (Object Oriented CSS)

객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론

**OOCSS** **기본 원칙**

1. **구조와 스킨을 분리**
    1. 구조와 스킨을 분리함으로써 재사용 가능성을 높임
        
        → 모든 버튼의 공통 구조를 정의 + 각각의 스킨(배경색과 폰트 색상)을 정의
        
        ![image.png](images/bt8.png)
        
         
        
2. **컨테이너와 콘텐츠를 분리**
    1. 객체에 직접 적용하는 대신 객체를 둘러싸는 컨테이너에 스타일을 적용
    2. 스타일을 정의할 때 위치에 의존적인 스타일을 사용하지 않도록 함
    3. 콘텐츠를 다른 컨테이너로 이동 시키거나 재 배치할 때 스타일이 깨지는 것을 방지
    
    ![image.png](images/bt9.png)
    

![image.png](images/bt10.png)

**의미론적인 마크업이 필요한 이유**

- 검색엔진 최적화(SEO)
    - 검색 엔진이 해당 웹 사이트를 분석하기 쉽게 만들어 검색 순위에 영향을 줌
- 웹 접근성(Web Accessibility)
    - 웹 사이트, 도구, 기술이 고령자나 장애를 가진 사용자들이 사용할 수 있도록 설계 및 개발하는 것 
    (ex. 스크린 리더를 통해 전맹 시각 장애 사용자에게 웹의 글씨를 읽어줌)
    - https://nuli.navercorp.com

## 참고

![image.png](images/bt11.png)

![image.png](images/bt12.png)

### emmet 시스템