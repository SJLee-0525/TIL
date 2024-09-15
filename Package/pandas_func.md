```python
import numpy as np
import pandas as pd
```

## 1. Pandas 로 csv 읽어오기

**기본**: pandas 에서 지원하는 데이터 파일을 읽어오는 함수

```python
df = pd.read_csv('data/test_data.CSV', encoding='cp949')
df.head()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36 | 남 | 기자 | 서울/경기 |
| 3 | 최성민 | 34 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45 | 남 | 모델 | 강원도 |

**parse_dates**: 열 이름을 넣어주면 데이터 타입을 datatime64[ns]로 변환해준다.

- `pd.to_datetime()` 함수로 datetime64 로 바꿀수도 있다.
- '2019-01-01' 같은 `String` 형태의 자료형을 `datetime64` 로 바꿀 수 있다.

---

**usecols**: 여러 열 중 필요한 열만 가져온다.

```python

df = pd.read_csv('data/test_data.CSV', encoding='cp949', usecols=['이름', '나이'])
df.head()
```

|  | 이름 | 나이 |
| --- | --- | --- |
| 0 | 김현우 | 25 |
| 1 | 이태현 | 28 |
| 2 | 박현준 | 36 |
| 3 | 최성민 | 34 |
| 4 | 정준우 | 45 |

---

**nrows**: 파일의 처음 n개의 행을 읽는다. 데이터 세트가 매우 큰 경우 유용하다.

```python
df = pd.read_csv('data/test_data.CSV', encoding='cp949', nrows=10)
df.shape
# (10, 5)
```

```python
df
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36 | 남 | 기자 | 서울/경기 |
| 3 | 최성민 | 34 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45 | 남 | 모델 | 강원도 |
| 5 | 김준혁 | 67 | 여 | 개발자 | 서울/경기 |
| 6 | 이지훈 | 32 | 여 | 카텐더 | 충청북도 |
| 7 | 박준영 | 24 | 남 | 학원강사 | 전라북도 |
| 8 | 최준서 | 34 | 여 | 개발자 | 강원도 |
| 9 | 정준호 | 54 | 남 | 화가 | 충청북도 |

---

## 2. value_counts

기본 함수에도 있던 함수. 범주형 열의 값 분포를 확인하는 데 유용하다.

발생 횟수와 함께 열의 고유 값을 반환한다.

```python
df = pd.read_csv('data/test_data.CSV', encoding='cp949')
df["성별"].value_counts()
'''
성별
남    26
여    24
Name: count, dtype: int64
'''
```

`normalize` 를 통해 분포를 비율로 확인할 수 있다.

```python
df["성별"].value_counts(normalize=True)
'''
성별
남    0.52
여    0.48
Name: proportion, dtype: float64
'''
```

---

## 3. astype

데이터 분석 전 데이터 타입을 적절한 것으로 변환하는 건 거의 필수다.

어떤 함수들은 적절한 데이터 타입에서 훨씬 더 효율적으로 동작하거나, 일부 함수들은 아예 특정 데이터 타입에서만 사용할 수 있다.

```python
df['이름'] = df['이름'].astype(str)
df.dtypes
'''
이름     object
나이      int64
성별     object
직업     object
사는곳    object
dtype: object
'''
```

string 형태는 object 로 출력된다.

여러 열의 데이터 타입을 한 번에 변경하려면 딕셔너리를 사용하면 된다.

```python
df = df.astype({'성별': 'category', '직업': 'str'})
df.dtypes
'''
이름       object
나이        int64
성별     category
직업       object
사는곳      object
dtype: object
'''
```

---

## 4. isna & notna

[참고] - na 는 Numpy 의 Na(Not a Number)값을 의미함

데이터에 비어있는 값(결측값) 이 존재하는 경우가 있다.

`test_data_has_null.CSV` 파일을 열어서 확인해보자.

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
df.head()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25.0 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28.0 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36.0 | 남 | NaN | 서울/경기 |
| 3 | 최성민 | 34.0 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45.0 | 남 | 모델 | 강원도 |

위와 같이 결측값은 `NaN` 으로 출력된다.

`isna` 함수와 `notna` 함수는 DataFrame 내의 결측값을 확인해서 `bool` 형식으로 반환하는 함수이다.

`isna` 의 경우 결측값이면 `True` 반환, 정상값이면 `False` 를 반환하며,

`notna` 의 경우 결측값이면 `False` 반환, 정상값이면 `True` 를 반환한다.

**주의사항**: 무한값(`np.inf`) 나 띄워쓰기`' '`의 경우 결측값으로 판단하지 않는다.

### isna

```python
df.head().isna()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | False | False | False | False | False |
| 1 | False | False | False | False | False |
| 2 | False | False | False | True | False |
| 3 | False | False | False | False | False |
| 4 | False | False | False | False | False |

### notna

```python
df.head().notna()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | True | True | True | True | True |
| 1 | True | True | True | True | True |
| 2 | True | True | True | False | True |
| 3 | True | True | True | True | True |
| 4 | True | True | True | True | True |

### 누락된 값의 수 구하기

```python
df.isna().sum()
'''
이름     0
나이     5
성별     1
직업     5
사는곳    2
dtype: int64
'''
```

### 행 별로 누락된 값의 수 구하기

```python
df.isna().sum(axis=1)
'''
0     0
1     0
2     1
3     0
4     0
5     0
6     1
7     0
8     0
9     0
10    0
11    0
12    0
13    1
14    0
15    0
16    0
17    0
18    0
19    0
20    1
21    0
22    0
23    2
24    0
...
46    0
47    1
48    0
49    0
dtype: int64
'''
```

### **isnull() vs isna()**

동일한 함수이다.
DB 에 저장된 결측치는 `null` 이라고 표시되는데, 이에 익숙한 사람들을 위해 `isna()` 의 별칭으로 `isnull()` 을 만들어 두었다.

---

이러한 결측치를 처리하는 2가지 방법이 존재한다.

- 버리기(Drop) - dropna
- 채우기(Fill) - fillna

## 5. dropna

첫 번째 방법으로, 누락된 값이 있는 행이나 열을 삭제하는 데 사용되는데, 다음 매개변수들이 존재한다.

참고사이트 - [pandas Docs - Dropna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html)

### axis

- **0** or **'index'** : 결측값이 있는 행을 삭제 -> default
- **1** or **'columns'** : 결측값이 있는 열을 삭제

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
```

```python
df.isna().sum()
'''
이름     0
나이     5
성별     1
직업     5
사는곳    2
dtype: int64
'''
```

`dropna()` 는 DataFrame 을 반환한다.
원본 DataFrame 을 변경하고 싶으면 `inplace=True` 를 설정해준다

```python
df.dropna(axis=0)
df.isna().sum()
'''
이름     0
나이     5
성별     1
직업     5
사는곳    2
dtype: int64
'''
```

```python
df.dropna(axis=0, inplace=True)
df.isna().sum()
'''
이름     0
나이     0
성별     0
직업     0
사는곳    0
dtype: int64
'''
```

---

### how

- **any**: row 또는 column 에 NaN 값이 1개만 있어도 drop -> default
- **all**: row 또는 column 에 있는 모든 값이 NaN 이어야 drop

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
df.dropna(axis=0, how='all', inplace=True)
df.isna().sum()
'''
이름     0
나이     5
성별     1
직업     5
사는곳    2
dtype: int64
'''
```

---

### thresh

- 결측값이 아닌 열이 몇 개 이상일 경우 삭제하지 않는다는 임계치(기준)을 설정한다.
- `axis=0, thresh=3` 일 때, 결측값이 아닌 열이 3개 이상이면 삭제하지 않는다.

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
df
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25.0 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28.0 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36.0 | 남 | NaN | 서울/경기 |
| 3 | 최성민 | 34.0 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45.0 | 남 | 모델 | 강원도 |
| 5 | 김준혁 | 67.0 | 여 | 개발자 | 서울/경기 |
| 6 | 이지훈 | 32.0 | 여 | NaN | 충청북도 |

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
df.dropna(axis=0, thresh=4, inplace=True)
df.isna().sum()
'''
이름     0
나이     4
성별     1
직업     4
사는곳    2
dtype: int64
'''
```

```python
df.shape
# (49, 5)
```

---

## 6. fillna

결측값을 다른 적절한 값으로 채워준다.

```python
df.head()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25.0 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28.0 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36.0 | 남 | NaN | 서울/경기 |
| 3 | 최성민 | 34.0 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45.0 | 남 | 모델 | 강원도 |

```python
df['직업'].fillna('무직', inplace=True)
df.head()
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 0 | 김현우 | 25.0 | 남 | 교수 | 경상남도 |
| 1 | 이태현 | 28.0 | 여 | 군인 | 경상북도 |
| 2 | 박현준 | 36.0 | 남 | **무직** | 서울/경기 |
| 3 | 최성민 | 34.0 | 남 | 리포터 | 강원도 |
| 4 | 정준우 | 45.0 | 남 | 모델 | 강원도 |

```python
df.isna().sum()
'''
이름     0
나이     4
성별     1
직업     0
사는곳    2
dtype: int64
'''
```

---

## 7. groupby

열의 고유한 값을 기반으로 행을 그룹화한다.

독립된 그룹에 대하여 **별도로 데이터를 처리** 하거나 **그룹별 통계량** 을 확인하고자 할 때 유용하다.

groupby 는 아래 3단계로 이루어 진다

![pandas-groupby-split-apply-combine.svg](https://prod-files-secure.s3.us-west-2.amazonaws.com/e00c77d9-eee7-4295-abdf-7606a77852a9/df5fd8ad-007a-4cbb-a035-24dac57b7236/pandas-groupby-split-apply-combine.svg)

![./data/pandas-groupby-split-apply-combine.svg](./data/pandas-groupby-split-apply-combine.svg)

**1. Split**: `.groupby()` 에서 정의한 컬럼 조건에 따라 독립된 그룹으로 나누는 단계. 위 사진에서는 `ID` 값을 기준으로 그룹으로 나누었고, 결과로 `X`, `Y`, `Z` 3개의 sub-group 으로 분할되었다.

**2. Apply**: sub-group 에 그룹별 함수를 적용하는 단계. 예시에서는 합계(sum) 함수를 적용하여 각 그룹 별 총계가 합산된 결과를 확인할 수 있다.

**3. Combine**: 각 sub-group 별로 함수가 적용된 결과를 종합하여 다시 하나의 테이블로 합침

이러한 과정을 이용하여 데이터 전처리/분석 시 유용하게 활용할 수 있다.

아래 예시는 `직업 별 평균 나이` 를 구하는 예시 코드이다.

```python
df = pd.read_csv('data/test_data_has_null.CSV', encoding='cp949')
df.groupby('직업').mean()
# TypeError: agg function failed [how->mean,dtype->object]
```

**참고 - 경고문**: 위의 함수는 평균치를 구하는 함수이다. 평균치라는 것은 숫자에 대해서만(`numeric_only`) 작동이 가능하기 때문에, 숫자로 이루어진 열에만 계산을 적용하라는 뜻으로 `numeric_only` 옵션이 기본적으로 `True` 로 설정되어 있다.

미래 버전에서는 해당 옵션 기본값이 `False` 로 변하므로, 직접 `True` 로 설정하여 버그를 없애라는 경고 문구이다.

아래와 같이 옵션을 지정하면 버그가 없어진다.

```python
df.groupby('직업').mean(numeric_only=True)
```

|  | 나이 |
| --- | --- |
| 직업 |  |
| 감정평가사 | 35.00 |
| 개발자 | 45.60 |
| 건축가 | 26.00 |
| 검사 | 15.00 |
| 게임기획자 | 78.00 |
| 교수 | 25.00 |
| 군인 | 28.00 |
| 대역배우 | NaN |
| 대학교수 | 73.00 |
| 도어맨 | 34.00 |
| 리포터 | 34.00 |
| 모델 | 41.00 |
| 미술가 | 34.00 |
| 법무사 | NaN |

위 코드는

1. 직업 별로 분할
2. 직업 별로 분할된 테이블의 숫자로 된 모든 열('나이') 의 평균 계산
3. 통합
을 통해 위와 같은 결과가 나온다

하나의 예시만 더 해보자.

`직업 별 평균 나이` 에서 `성별을 추가적으로 구분하여 출력` 하는 예시 코드이다.

```python
df.groupby(['직업', '성별']).mean(numeric_only=True).reset_index()
# reset_index()는 인덱스를 원상태로 반환해줌?
```

|  | 직업 | 성별 | 나이 |
| --- | --- | --- | --- |
| 0 | 감정평가사 | 남 | 35.000000 |
| 1 | 개발자 | 남 | 50.666667 |
| 2 | 개발자 | 여 | 43.428571 |
| 3 | 건축가 | 남 | 25.000000 |
| 4 | 검사 | 남 | 15.000000 |
| 5 | 검사 | 여 | NaN |
| 6 | 게임기획자 | 여 | 78.000000 |
| 7 | 교수 | 남 | 25.000000 |
| 8 | 군인 | 여 | 28.000000 |
| 9 | 대역배우 | 남 | NaN |
| 10 | 대학교수 | 여 | 73.000000 |
| 11 | 도어맨 | 남 | 34.000000 |
| 12 | 리포터 | 남 | 34.000000 |
| 13 | 모델 | 남 | 41.000000 |
| 14 | 미술가 | 남 | 34.000000 |
| 15 | 법무사 | 여 | NaN |
| 16 | 변호사 | 남 | 76.000000 |

이와 같이 여러 그룹으로 구분하여, 여러가지 통계적인 계산이나 수학 연산 등이 가능하다.

아래 Docs 를 참고하여 여러 예제 코드를 사용해보자.

[Pandas Docs - Groupby](https://pandas.pydata.org/docs/reference/groupby.html) 참고

---

## 8. unique & nunique

- **unique**: 고유값의 종류를 모두 출력
- **nunique**: 고유값의 개수를 반환

```python
df['직업'].unique()
'''
array(['교수', '군인', nan, '리포터', '모델', '개발자', '학원강사', '화가', '변호사', '법무사',
       '판사', '검사', '미술가', '게임기획자', '프로게이머', '감정평가사', '빅데이터전문가', '대학교수',
       '대역배우', '도어맨', '패션모델', '휴대폰디자이너', '웹디자이너', '웹개발자', '건축가'],
      dtype=object)
      '''
```

```python
df['직업'].nunique()
# 24
```

---

## 9. 정렬

- `sort_values()` 함수를 사용한다

9.1. 정렬의 기준은 기본적으로 오름차순이다

```python
df['직업'].sort_values()
'''
28      감정평가사
49        개발자
41        개발자
5         개발자
29        개발자
8         개발자
27        개발자
48        개발자
12        개발자
22        개발자
17        개발자
47        건축가
44        건축가
20         검사
19         검사
25      게임기획자
0          교수
1          군인
34       대역배우
32       대학교수
36        도어맨
3         리포터
46         모델
4          모델
21        미술가
...
6         NaN
23        NaN
31        NaN
43        NaN
Name: 직업, dtype: object
'''
```

9.2. 내림차순은 `ascending=False` 옵션을 추가해준다.

```python
df['직업'].sort_values(ascending=False)
'''
39    휴대폰디자이너
9          화가
10       학원강사
15       학원강사
35       학원강사
18       학원강사
7        학원강사
24       학원강사
26      프로게이머
38       패션모델
16         판사
40      웹디자이너
42       웹개발자
45    빅데이터전문가
37    빅데이터전문가
30    빅데이터전문가
33    빅데이터전문가
14        변호사
11        변호사
13        법무사
21        미술가
46         모델
4          모델
3         리포터
36        도어맨
...
6         NaN
23        NaN
31        NaN
43        NaN
Name: 직업, dtype: object
'''
```

9.3. 모든 컬럼을 보기 위해서는 `by` 옵션을 활용한다.

```python
df.sort_values(by=['나이'])
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 19 | 정지윤 | 15.0 | 남 | 검사 | 서울/경기 |
| 30 | 김태현 | 17.0 | 남 | 빅데이터전문가 | 전라북도 |
| 10 | 김지은 | 23.0 | 여 | 학원강사 | 경상북도 |
| 41 | 김태우 | 23.0 | 여 | 개발자 | 강원도 |
| 7 | 박준영 | 24.0 | 남 | 학원강사 | 전라북도 |
| 16 | 이은서 | 25.0 | 남 | 판사 | 경상북도 |
| 44 | 최지훈 | 25.0 | 남 | 건축가 | 경상북도 |
| 0 | 김현우 | 25.0 | 남 | 교수 | 경상남도 |

9.4. 두 가지 이상의 정렬을 하는 방법은 다음과 같다.

- 직업 별 오름차순, 나이 별 내림차순
- ascending 옵션을 정렬 필드 순서대로 각각 지정해준다.

```python
df.sort_values(by=['직업', '나이'], ascending=[True, False])
```

|  | 이름 | 나이 | 성별 | 직업 | 사는곳 |
| --- | --- | --- | --- | --- | --- |
| 28 | 최민서 | 35.0 | 남 | 감정평가사 | 경상북도 |
| 5 | 김준혁 | 67.0 | 여 | 개발자 | 서울/경기 |
| 29 | 정은서 | 67.0 | 여 | 개발자 | 제주도 |
| 12 | 박지현 | 64.0 | 남 | 개발자 | 강원도 |
| 27 | 박예린 | 45.0 | 남 | 개발자 | 제주도 |
| 22 | 박수진 | 43.0 | 여 | 개발자 | 전라남도 |
| 49 | 김장고 | 43.0 | 남 | 개발자 | 서울/경기 |
| 48 | 백엔드 | 36.0 | 여 | 개발자 | 서울/경기 |