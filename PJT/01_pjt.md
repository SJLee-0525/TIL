# 01 PJT  

**클라이언트 ↔ 서버**

- **서버**: 요청을 받으면 처리하거나, 원하는 정보를 돌려주는 역할
- **클라이언트**: 정보를 요청하는 역할 (고객)

## **서버에 정보 요청하기**

1. **웹 브라우저를 켜서 주소 창에 URL을 입력한다.** 
     
    [https://fakestoreapi.com/]   
    [https://fakestoreapi.com/carts]
    
    서버 주소 **/** 요청 주소
    
2. **서버에 정보를 요청하는 파이썬 코드를 작성한다.**

```python
# requests: 파이썬에서 서버에 요청을 보낼 수 있는 도구

$ pip install requests # 설치 
```

## PIP

**파이썬 패키지 관리 시스템: 설치, 삭제 담당**

- **최신 버전 / 특정 버전 / 최소 버전을 명시하여 설치할 수 있음**

```python
$ pip install SomePackage # 최신 버전

$ pipinstallSomePackage==1.0.5 # 특정 버전

$ pip install SomePackage>=1.0.4 # 최소 버전 명시

$ pip list # 설치된 패키지 목록 확인
```

- **requests 외부 패키지 설치 및 사용 예시**

```python
**# 외부 API에게 자료를 요청할 때 사용**
**$ pip install requests** 

**import requests**

**url = "https://fakestoreapi.com/carts"** # 요청을 보내는 서버의 주소
**data = requests.get(url).json()** # requests 안에 있는 get 함수에 접근한다.
# **requests의 .json이 JSON 형태(python의 dict와 유사)로 전환해줌**: 원래는 문자열임
# 요청, 응답, 변환 다 해주는 코드니 기억하기

data = requests.get(url).json()
```

- **위 방식대로 패키지 설치 시 글로벌에 설치가 됨: 전역 설치**

## API

**`내 코드 <-> API <-> DATA`**

**클라이언트가 원하는 기능을 수행하기 위해서 서버 측에 만들어 놓은 프로그램**

- 기능 예시: 데이터 저장, 조회, 수정 삭제 등

**서버 측에 특정 주소로 요청이 오면 정해진 기능을 수행하는 API를 미리 만들어 둠**

- 클라이언트는 서버가 미리 만들어 놓은 주소로 요청을 보냅니다.

### Open API

- 외부에서 사용할 수 있도록 **무료로 개방된 API**
- 사용법은 **공식 문서(Docs)**에 명시되어 있음
- 프로젝트에서 사용되는 API
    - **([OpenWeatherMap API](https://openweathermap.org/))**
    - **금융상품통합비교공시 API**
    - **알라딘, Spotify 등**  

  
**주의 사항:**

- 너무 많은 계정에서 동시에 요청을 보내면 서버가 견디지 못함
    - 오픈 API는 **API KEY**를 활용해 사용자를 확인
        - 인증 및 회원 가입 시 서버에서 API KEY 발급
        - 요청할 때마다 API KEY를 보내 정상적인 사용자를 확인
    - 일부 오픈 API는 **사용량이 제한됨**
        - 공식 문서의 일일 및 월간 사용량 제한을 반드시 확인
        - 사용량 초과 시 요금이 청구될 수 있으니 주의

### JSON

**JavaScript Object Notation**

- 데이터를 저장하거나 전송할 때 많이 사용되는 **경량의 텍스트 기반 데이터 형식**
- 단순히 **데이터를 표현하는 표현 방법** 중 하나
- **특징 (Dict와 유사: 하지만 문자열임)**
    - { }로 둘러싸인 Key - Value 쌍의 집합
    - Key = 문자열 / Value = 다양한 데이터 유형을 가질 수 있음
    - 값은 쉼표로 구분
- **참고:**
    - **Parsing:** 데이터를 의미 있는 구조로 분석하고 해석하는 과정
    - **json.loads():** json 형식의 문자열을 파싱하여 python dictionary로 반환

버전1 : 

날씨 데이터 수집 및 미션 수행