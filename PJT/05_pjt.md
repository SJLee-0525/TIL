## 파이썬으로 웹 페이지에 있는 정보를 가져오는 방법

1. 누군가 업로드해 둔 데이터를 다운로드 받기 (ex. 캐글)
2. 누군가 만들어 둔 API Server를 활용해서 정보를 받아오기: API가 없을지도
3. **사람이 검색하는 것처럼 파이썬이 자동으로 검색 후 결과를 수집하기: 크롤링(Crawling)**

# 복습

## 데이터 사이언스 프로세스

1. **문제 정의:** 해결하고자 하는 문제 정의
2. **데이터 수집:** 문제 해결에 필요한 데이터 수집
3. **데이터 전처리:** 실질적인 분석을 수행하기 위해 데이터를 가공
    - 수집한 데이터의 오류 제거(결측치, 이상치), 데이터 형식 변환 등
4. **데이터 분석:** 전처리가 완료된 데이터에서 필요한 정보를 추출
5. **결과 해석 및 공유:** 의사 결정에 활용하기 위해 결과를 해석하고 시각화 후 공유

## 데이터 수집

- **웹 스크래핑(Web Scraping):** 웹 페이지에서 데이터를 추출 (한 페이지)
- **웹 크롤링(Web Crawling):** 웹 페이지를 자동으로 탐색하고 데이터를 수집 (여러 페이지, 자동화)
- **Open API 활용:** 공개된 API를 통해 데이터를 수집
- **데이터 공유 플랫폼 활용:** 다양한 사용자가 데이터를 공유하고 활용할 수 있는 온라인 플랫폼
    - 캐글(Kaggle), Data World, 데이콘(Dacon), 공공데이터포털 등

# 웹 크롤링

- 여러 웹 페이지를 돌아다니며 원하는 정보를 모으는 기술
- 원하는 정보를 추출하는 스크래핑(Scraping)과 여러 웹페이지를 자동으로 탐색하는 크롤링(Crawling)의 개념을 합쳐 웹 크롤링이라고 부름

**→ 웹 사이트를 돌아다니며 필요한 데이터를 추출해 활용할 수 있도록 자동화된 프로세스**

## 웹 크롤링 프로세스

- **웹 페이지 다운로드**
    - 해당 웹 페이지의 HTML, CSS, JavaScript 등의 코드를 가져오는 단계
- **페이지 파싱**
    - 다운로드 받은 코드를 분석하고 필요한 데이터를 추출하는 단계
- **링크 추출 및 다른 페이지 탐색**
    - 다른 링크를 추출하고, 다음 단계로 이동해 원하는 데이터를 추출하는 단계
- **데이터 추출 및 저장**
    - 분석 및 시각화에 사용하기 위해 데이터를 처리하고 저장하는 단계

## 실습

### 필수 라이브러리

```bash
$ pip install requests beautifulsoup4 selenium
```

- **`requests` : HTTP 요청을 보내고 응답을 받을 수 있는 모듈**
- **`BeautifulSoup` : HTML 문서에서 원하는 데이터를 추출**하는 데 사용되는 파이썬 라이브러리
- **`Selenium` : 웹 애플리케이션을 테스트하고 자동화**하기 위한 파이썬 라이브러리
    - 웹 페이지의 동적인 컨텐츠를 가져오기 위해 사용 (검색 결과 등)

### 기본 예제 실습

- https://quotes.toscrape.com/ 사이트 활용
    - 여러 가지 주제에 관한 명언들을 모아 둔 데모 사이트
- `requests` , `BeautifulSoup` 라이브러리 활용 연습
    - examples/example.py

```python
from bs4 import BeautifulSoup
import requests

def crawling_basic():
    # 가져올 url 문자열로 입력
    url = 'http://quotes.toscrape.com/tag/love/'  

    # requests의 get함수를 이용해 해당 url로 부터 html이 담긴 자료를 받아옴
    response = requests.get(url)    

    print('response = ', response)
    # response =  <Response [200]>

    # 우리가 얻고자 하는 html 문서가 여기에 담기게 됨
    html_text = response.text
    print(type(html_text)) # <class 'str'>
    print(html_text) # 문자열: 구조화가 안 되어있음
    '''
    <!DOCTYPE html>
    <html lang="en">
    <head>
            <meta charset="UTF-8">
            <title>Quotes to Scrape</title>
        <link rel="stylesheet" href="/static/bootstrap.min.css">
        <link rel="stylesheet" href="/static/main.css">
    </head>
    <body>
    </body>
    </html>
    '''

    # html을 잘 정리된 형태로 변환 (parsing을 하기 위해)
    soup = BeautifulSoup(html_text, 'html.parser')
    print(type(soup)) # <class 'bs4.BeautifulSoup'> beautifulsoutp가 제공하는 객체로 변환
    print(soup)
    '''
    # 들여쓰기 사라짐?
    <!DOCTYPE html>

    <html lang="en">
    <head>
    <meta charset="utf-8"/>
    <title>Quotes to Scrape</title>
    <link href="/static/bootstrap.min.css" rel="stylesheet"/>
    <link href="/static/main.css" rel="stylesheet"/>
    </head>
    <body>
    </body>
    </html>
    '''
    print(soup.prettify()) # 들여쓰기 돌아옴

    # 1. 태그를 이용하여 하나 검색
    main = soup.find('a')
    print(f'제목 : {main}')      # 제목 : <a href="/" style="text-decoration: none">Quotes to Scrape</a>
    print(f'제목 : {main.text}') # 제목 : Quotes to Scrape

    # 2. 해당 태그인 모든 요소 검색
    a_tags = soup.find_all('a') # 리스트 형태로 반환: 반복문 가능!
    print(f'a 태그 : {a_tags}') # a 태그 : [<a href="/" style="text-decoration: none">Quotes to Scrape</a>, <a href="/login">Login</a>, ..., <a class="zyte" href="https://www.zyte.com">Zyte</a>]

    for tag in a_tags:
        print(f'태그: {tag.text}')
    '''
    태그: Quotes to Scrape
    태그: Login
    ...,
    태그: Zyte
    '''

    # 3. CSS 선택자로 하나 검색
    # 선택자가 일치하는 첫 번째글 (가장 처음 만나는 것을 골라 줌)
    word = soup.select_one('.text')
    print(f'첫 번째 글 = {word.text}') # 첫 번째 글 = “It is better to be hated for what you are than to be loved for what you are not.”

    # 4. CSS 선택자로 여러 개 검색하기
    words = soup.select('.text')
    for w in words:
        print(f'글 : {w.text}')
    '''
    글 : “It is better to be hated for what you are than to be loved for what you are not.”
    ...,
    글 : “Love does not begin and end the way we seem to think it does. Love is a battle, love is a war; love is a growing up.”
    글 : “There is nothing I would not do for those who are really my friends. I have no notion of loving people by halves, it is not my nature.”
    '''

    # 예쁘게 출력하기
    print(soup.prettify())

crawling_basic()

```

### 구글 검색 결과 크롤링 해보기

```python
from bs4 import BeautifulSoup
import requests

def crawling_basic():
    # 가져올 url 문자열로 입력
    url = 'https://www.google.com/search?q=%ED%83%95%EC%88%98%EC%9C%A1&sca_esv=1d9a3a092ad1c62b&hl=ko&source=hp&ei=3Dr_ZtLEHqWovr0P5OyMwQ0&iflsig=AL9hbdgAAAAAZv9I7FNNip95lvngePLjd_wTlvyyChBf&ved=0ahUKEwjSopz_v_OIAxUllK8BHWQ2I9gQ4dUDCA8&uact=5&oq=%ED%83%95%EC%88%98%EC%9C%A1&gs_lp=Egdnd3Mtd2l6Igntg5XsiJjsnKEyCBAuGIAEGLEDMgsQABiABBixAxiDATIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESJIYUB5YixdwCXgAkAECmAHjAaABmw2qAQUwLjguMrgBA8gBAPgBAZgCCaACjQWoAgDCAg0QABiABBixAxiDARgKwgIHEAAYgAQYCsICDRAuGIAEGNEDGMcBGArCAgQQABgDwgILEC4YgAQYsQMYgwHCAgQQLhgDwgIIEAAYgAQYsQPCAgUQLhiABMICCxAuGIAEGNEDGMcBwgILEC4YgAQYxwEYrwHCAhEQLhiABBixAxjRAxiDARjHAZgDApIHBTYuMS4yoAewVw&sclient=gws-wiz'  

    # requests의 get함수를 이용해 해당 url로 부터 html이 담긴 자료를 받아옴
    response = requests.get(url)    

    html_text = response.text
    # print(html_text) # 눈으로 보기가 너무 힘듬

    # crawling_examples/soup.txt 생성
    with open('soup.txt', 'w', encoding='utf-8') as file:
        file.write(html_text)

    **# requests 모듈은 정적인 부분만 다운로드 가능 > 동적인 컨텐츠를 다운로드 받을 수 없음
    # 정적이다? 서버가 이미 가지고 있는 데이터만.
    # 동적인 부분: 탕수육이라는 결과를 통해서 변경되는 부분 (검색어 등)

    # selenium: 개발자들이 동적 웹 테스트를 위해 많이 사용, 동적인 컨텐츠를 받을 수 있음 -> 크롤링에서 활**

crawling_basic()
```

**`selenium` 활용해서 웹 페이지 크롤링 하기**

```python
from bs4 import BeautifulSoup
from selenium import webdriver

def get_google_data(keyword):
    url = f"https://www.google.com/search?q={keyword}"

    # 크롬 브라우저가 열린다. 이 때, 동적인 내용들이 모두 채워짐
    driver = webdriver.Chrome()
    driver.get(url)

    # 열린 페이지 소스를 받아옴
    html = driver.page_source # 문자열 데이터를 다운로드
    soup = BeautifulSoup(html, "html.parser") # 파싱을 위해 변환
    
    # 눈으로 보기 좋게 출력
    print(soup.prettify())

    # 파일로 저장하여 확인하기
    with open('soup.txt', 'w', encoding="utf-8") as file:
        file.write(soup.prettify())

    driver.quit()

# 검색 키워드 설정
keyword = "탕수육"
get_google_data(keyword)
```

**요소 검색하기 (id 활용 `#`)**

```python
from bs4 import BeautifulSoup
from selenium import webdriver

def get_google_data(keyword):
    url = f"https://www.google.com/search?q={keyword}"
    # 크롬 브라우저가 열린다. 이 때, 동적인 내용들이 모두 채워짐
    driver = webdriver.Chrome()
    # driver = webdriver.Chrome()
    driver.get(url)

    # 열린 페이지 소스를 받아옴
    html = driver.page_source 
    soup = BeautifulSoup(html, "html.parser")

    # div 태그 중 id 가 result-stats 인 요소 검색
    result_stats = soup.select_one("div#result-stats")
    print(result_stats.text)

    driver.quit()

# 검색 키워드 설정
keyword = "탕수육"
get_google_data(keyword)

'''
$ python example2.py 

DevTools listening on ws://127.0.0.1:57154/devtools/browser/ee510b0f-6f4d-434d-b8bd-c786afdb1439
검색결과 약 6,320,000개 (0.24초) 
'''
```

**요소 검색하기 (class 활용 `.`) + 반복**

```python
from bs4 import BeautifulSoup
from selenium import webdriver

def get_google_data(keyword):
    url = f"https://www.google.com/search?q={keyword}"
    # 크롬 브라우저가 열린다. 이 때, 동적인 내용들이 모두 채워짐
    driver = webdriver.Chrome()
    # driver = webdriver.Chrome()
    driver.get(url)

    # 열린 페이지 소스를 받아옴
    html = driver.page_source 
    soup = BeautifulSoup(html, "html.parser")

    # div 태그 중 g 클래스를 가진 모든 요소 선택
    g_list = soup.select("div.g")
    # 해당 요소를 반복하며
    for g in g_list:
        # 요소 안에 LC20lb MBeuO DKV0Md 클래스를 가진 특정 요소 선택
        title = g.select_one(".LC20lb.MBeuO.DKV0Md")
        # 요소가 존재 한다면
        if title is not None:
            title_text = title.text
            print('제목 = ', title_text)

# 검색 키워드 설정
keyword = "탕수육"
get_google_data(keyword)

'''
$ python example3.py 

DevTools listening on ws://127.0.0.1:57197/devtools/browser/026c9082-62c1-4144-a948-975553105d48
제목 =  탕수육
제목 =  초보도 성공하는 돼지고기 탕수육
제목 =  크레잇 찹쌀등심탕수육 스틱형1kg | 상품상세
제목 =  집에서 간단히 만드는 탕수육 황금레시피
제목 =  탕수육 - 위키백과, 우리 모두의 백과사전
제목 =  검색결과 >탕수육, 이마트몰, 당신과 가장 가까운 이마트 - SSG
제목 =  [모노키친] 베이징풍 찹쌀탕수육
제목 =  고메 탕수육 450g | 상품상세
'''
```

## BeautifulSoup4 요소 선택 메서드 종류

- **`find()`**
    - 태그를 사용해서 요소를 검색 후 첫 번째로 일치하는 요소를 반환
- **`find_all()`**
    - 태그를 사용해서 요소를 검색 후 일치하는 모든 요소를 리스트로 반환
- **`select()`**
    - CSS 선택자를 사용해서 요소를 검색 후 일치하는 모든 요소를 리스트로 반환
- **`select_one()`**
    - CSS 선택자를 사용해서 요소를 검색 후 첫 번째로 일치하는 요소를 반환
- **`find_parent()` / `find_next_sibling()` / `find_previous_sibling()`**
    - 태그를 사용해서 요소를 검색 후 
    각각 `일치하는 요소의 부모` / `다음 형제 요소` / `이전 형제 요소` 를 반환

## Django에서 활용

```python
# crawlings/models.py

from django.db import models

class Article(models.Model):
    query = models.TextField()
    title = models.TextField()

# 정석 버전(최적화 되어있음)
# class Article(models.Model):
#     title = models.TextField()

# # 하나의 query로 여러 개의 게시글을 검색할 수 있음
# class Query(models.Model):
#     article = models.ForeignKey(Article, on_delete=models.DO_NOTHING)
#     name = models.TextField()
```

```python
# crawlings/urls.py

from django.urls import path
from . import views

app_name="crawlings"
urlpatterns = [
    path('', views.index, name="index"),
]
```

```python
# crawlings/views.py

from django.shortcuts import render
from .models import Article

from bs4 import BeautifulSoup
from selenium import webdriver

def index(request):
    # 사용자가 검색을 하면 크롤링을 진행
    if request.method == 'POST':
        result = [] # 검색 결과
        query = request.POST.get('query')
        titles = get_google_data(query)
        # print(titles)
        '''
        ['탕수육', '초보도 성공하는 돼지고기 탕수육', '집에서 간단히 만드는 탕수육 황금레
        시피', '크레잇 찹쌀등심탕수육 스틱형1kg | 상품상세', '탕수육 - 위키백과, 우리 모두
        의 백과사전', '검색결과 >탕수육, 이마트몰, 당신과 가장 가까운 이마트 - SSG', '[모 
        노키친] 베이징풍 찹쌀탕수육', '고메 탕수육 450g | 상품상세']
        [04/Oct/2024 10:45:20] "POST /crawlings/ HTTP/1.1" 200 698
        '''

        for title in titles:
            # # Article 저장
            # Article.objects.create(query=query, title=title)

            # # Article을 저장(단, 중복 허용 X)
            # if Article.objects.filter(query=query, title=title).exists():
            #     Article.objects.create(query=query,title=title)

            # DB에 있으면 가져오고, 없으면 저장하는 메서드
            article, created_article = Article.objects.get_or_create(query=query, title=title)
    
    context = {
        'results': Article.objects.all()
    }

    # 아니라면 그냥 검색 페이지를 제공
    return render(request, 'crawlings/index.html', context)

def get_google_data(keyword):
    url = f"https://www.google.com/search?q={keyword}"
    # 크롬 브라우저가 열린다. 이 때, 동적인 내용들이 모두 채워짐
    driver = webdriver.Chrome()
    # driver = webdriver.Chrome()
    driver.get(url)

    # 열린 페이지 소스를 받아옴
    html = driver.page_source 
    soup = BeautifulSoup(html, "html.parser")

    # div 태그 중 g 클래스를 가진 모든 요소 선택
    g_list = soup.select("div.g")

    titles = []
    # 해당 요소를 반복하며
    for g in g_list:
        # 요소 안에 LC20lb MBeuO DKV0Md 클래스를 가진 특정 요소 선택
        title = g.select_one(".LC20lb.MBeuO.DKV0Md")
        # 요소가 존재 한다면
        if title is not None:
            title_text = title.text
            titles.append(title_text)

    return titles
```

```html
<!-- crawlings/templates/crawlings/index.html -->

{% extends "base.html" %}

{% block content %}

<h1>메인 페이지</h1>
{% if request.user.is_authenticated %}
  <form action="{% url "crawlings:index" %}" method='POST'>
    {% csrf_token %}
    <label for="query">검색어: </label>
    <input type="text" name='query'>
    <input type="submit" value='검색'>
    {% comment %} <button>검색하기</button> {% endcomment %}
    {% comment %} button은 자동으로 submit 됨 {% endcomment %}

    {% for result in results %}
    <p>{{ forloop.counter }}: {{ result.title }}</p>
    <hr>
    {% endfor %}
  </form>
{% else %}
  <h3>먼저 로그인 해 주세요</h3>
{% endif %}
{% endblock content %}

```