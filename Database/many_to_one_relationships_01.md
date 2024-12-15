# Many to one relationships

한 테이블의 0개 이상의 레코드가 다른 테이블의 레코드 한 개와 관련된 관계

## 모델 관계

### **`Comment(N) - Article(1)`**

- 0개 이상의 댓글은 1개의 게시글에 작성될 수 있음

**테이블 관계**

![image.png](images/mto_1_1.png)

## 댓글 모델 정의

### `ForeignKey()`

**한 모델이 다른 모델을 참조하는 관계를 설정하는 필드 : `N:1 관계 표현`**

→  데이터 베이스에서 외래 키로 구현

```python
# articles/models.py

from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

**class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    content = models.CharField(max_length=200)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)**
```

- **`ForeignKey`** 클래스의 인스턴스 이름은 모델 클래스 이름의 단수형으로 작성하는 것을 권장
- 외래 키는 **`ForeignKey`** 클래스를 작성하는 위치와 관계 없이 테이블의 마지막 필드로 생성됨

**`ForeignKey(to, on_delete)`**

- **`to`**
    - 참조하는 모델 class 이름
- **`on_delete`**
    - 외래 키가 참조하는 객체(1)가 사라졌을 때,
    외래 키를 가진 객체(N)를 어떻게 처리할 지를 정의하는 설정 (데이터 무결성)
    - **`CASCADE`** : 참조된 객체(부모 객체)가 삭제될 때 이를 참조하는 모든 객체도 삭제하도록 지정
    - **`SET_NULL` , `SET_DEFAULT` …**
        - https://docs.djangoproject.com/en/4.2/ref/models/fields/#arguments

**Migration 이후 댓글 테이블 확인**

- 댓글 테이블의 **`article_id`** 외래 키 필드 확인
- 만들어지는 필드 이름
    
    ![image.png](images/mto_1_2.png)
    
    - **`'참조 대상 클래스 이름' + '_' + 클래스 이름'`**
        
        →  참조하는 클래스 이름의 소문자(단수형)로 작성되는 것이 권장됐던 이유
        

## 댓글 생성 연습

1. **`shell_plus` 실행 및 게시글 작성**
    
    ```bash
    # shell_plus 실행
    $ python manage.py shell_plus 
    
    # 게시글 생성
    In [1]: Article.objects.create(title='title', content='content')
    Out[1]: <Article: Article object (1)>
    ```
    

1. **댓글 생성**
    
    ```bash
    # Comment 클래스의 인스턴스 comment 생성
    In [2]: comment = Comment() 
    
    # 인스턴스 변수 저장
    In [3]: comment.content = 'first comment'
    
    # DB에 댓글 저장
    In [4]: comment.save()
    
    # 에러 발생
    IntegrityError: NOT NULL constraint failed: articles_comment.article_id
    	=> # articles_comment 테이블의 ForeignKeyField, article_id 값이 저장 시 누락됐기 때문
    		=> # 어떤 게시글에 댓글을 달지 정하지 않았기 때문
    ```
    

1. **`shell_plus` 실행 및 게시글 작성**
    
    ```bash
    # 게시글 조회
    In [5]: article = Article.objects.get(pk=1)
    
    # 외래 키 데이터 입력
    In [6]: comment.article = article
    # 또는 comment.article_id = article.pk 표현으로 
    # pk 값을 직접 외래 키 칼럼에 넣어줄 수도 있지만 권장하지 않음.
    
    # In [3]: comment.content = 'first comment'
    
    # 댓글 저장 및 확인
    In [7]: comment.save()
    
    In [8]: Comment.objects.all()
    **Out[8]: <QuerySet [<Comment: Comment object (1)>]>**
    ```
    
    ![image.png](images/mto_1_3.png)
    

1. **`comment` 인스턴스를 통한 `article` 값 참조하기**
    
    ```bash
    In [9]: comment.pk
    Out[9]: 1
    
    In [10]: comment.content
    Out[10]: 'first comment'
    
    # 클래스 변수명인 article로 조회 시 해당 참조하는 게시글 객체를 조회할 수 있음
    In [11]: comment.article
    Out[11]: <Article: Article object (1)>
    
    # article_pk는 존재하지 않는 필드이기 때문에 사용 불가
    In [12]: comment.article_id
    Out[12]: 1
    
    # 1번 댓글이 작성된 게시글의 content 조회
    In [13]: comment.article.content
    Out[13]: 'content'
    ```
    

1. **2번째 댓글 생성**
    
    ```bash
    In [15]: comment = Comment(content='second comment', article=article)
    
    In [16]: comment.save()
    
    In [17]: comment
    Out[17]: <Comment: Comment object (2)>
    
    # 2번 댓글이 작성된 게시글의 pk 조회
    In [20]: comment.article.pk
    Out[20]: 1
    ```
    

1. **작성된 댓글 데이터 확인**
    
    ![image.png](images/mto_1_4.png)
    

# 관계 모델 참조

## 역 참조

- **`N:1` 관계에서 `1`에서 `N`을 참조하거나 조회하는 것 `(1 → N)`**
- 모델 간의 관계에서 관계를 정의한 모델이 아닌,
관계의 대상이 되는 모델에서 연결된 객체들에 접근하는 방식
    
    **→ `N`은 외래 키를 가지고 있어 물리적으로 참조가 가능하지만,
        `1`은 `N`에 대한 참조 방법이 존재하지 않아 별도의 역 참조 키워드가 필요**
    

### 역참조 사용 예시

**`article.comment_set.all()`**

- **모델 인스턴스**
- **related manager (역 참조 이름)**
- **QuerySet API**
    
    **→ 특정 게시글에 작성된 댓글 전체를 조회하는 요청**
    

### `related manager`

**N:1 혹은 M:N 관계에서 역참조 시에 사용하는 매니저**

→ `objects` 매니저를 통해 QuerySet API를 사용했던 것처럼
    `related manager` 를 통해 QuerySet API를 사용할 수 있게 됨

**related manager 이름 규칙**

- **`N:1`** 관계에서 생성되는 **`Related manager`** 의 이름은 **`“모델명_set”`** 형태로 자동 생성됨
    - 관계를 직접 정의하지 않은 모델에서 연결된 객체들을 조회할 수 있게 함
- 특정 댓글의 게시글 참조 (Comment → Article)
    - **`comment.article`**
- 특정 게시글의 댓글 목록 참조 (Article → Comment)
    - **`article.comment_set.all()`**

**related manager 연습**

```bash
# shell_plus 실행 및 1번 게시글 조회
In [22]: article = Article.objects.get(pk=1)

# 1번 게시글에 작성된 모든 댓글 조회하기 (역참조)
In [23]: article.comment_set.all()
Out[23]: <QuerySet [<Comment: Comment object (1)>, <Comment: Comment object (2)>]>

# 1번 게시글에 작성된 모든 댓글 내용 출력
In [25]: for comment in comments:
    ...:     print(comment.content)
    ...: 
first comment
second comment
```

## 댓글 구현

### 댓글 CREATE

1. **사용자로부터 댓글 데이터를 입력 받기 위한 `CommentForm` 정의**
    
    ```python
    # articles/forms.py
    
    from django import forms
    from .models import Article, Comment
    
    class ArticleForm(forms.ModelForm):
        class Meta:
            model = Article
            fields = '__all__'
    
    class CommentForm(forms.ModelForm):
        class Meta:
            model = Comment
            fields = '__all__'
    ```
    

1. detail view 함수에서 `CommentForm` 을 사용해서 detail 페이지에 렌더링
    
    ```python
    # articles/views.py
    
    from .models import Article
    from .forms import ArticleForm, CommentForm
    
    def detail(request, pk):
        article = Article.objects.get(pk=pk)
        comment_form = CommentForm()
        context = {
            'article': article,
            'comment_form': comment_form,
        }
        return render(request, 'articles/detail.html', context)
    ```
    
    ```html
    <!-- articles/detail.html -->
    
    <form action="#" method='POST'>
      {% csrf_token %}
      {{ comment_form }}
      <input type="submit">
    </form>
    ```
    

1. 결과 출력
    
    ![image.png](images/mto_1_5.png)
    
    - `Comment` 클래스의 외래 키 필드 `article` 또한 
    데이터 입력이 필요한 필드이기 때문에 출력되는 것
    - 하지만 외래 키 필드 데이터는 사용자로부터 입력 받는 값이 아닌
    view 함수 내에서 다른 방법으로 전달 받아 저장되어야 함

1. `CommentForm` 의 출력 필드 조정해 외래 키 필드가 출력되지 않도록 함
    
    ```python
    # articles/forms.py
    
    from django import forms
    from .models import Article, Comment
    
    class ArticleForm(forms.ModelForm):
        class Meta:
            model = Article
            fields = '__all__'
    
    class CommentForm(forms.ModelForm):
        class Meta:
            model = Comment
            **fields = ('content',)**
    ```
    
    ![image.png](images/mto_1_6.png)
    
    - 출력에서 제외된 외래 데이터는 어디서 받아와야 할까?
        - detail 페이지의 URL: **`path('<int:pk>/', views.detail, name='detail')`**
            
            URL에서 해당 게시글의 pk 값이 사용되고 있음
            
            **→ 댓글의 외래 키 데이터에 필요한 정보가 바로 게시글의 pk 값**
            
    

1. url 작성 및 action 값 작성
    
    ```python
    # articles/urls.pk
    
    from django.urls import path
    from . import views
    
    app_name = 'articles'
    urlpatterns = [
    		...
        path('<int:pk>/update/', views.update, name='update'),
        **path('<int:pk>/comments/', views.comments_create, name='comments_create'),**
    ]
    ```
    
    ```html
    <!-- articles/detail.html -->
    
    <form action="{% url "articles:comments_create" article.pk %}" method='POST'>
      {% csrf_token %}
      {{ comment_form }}
      <input type="submit">
    </form>
    ```
    

1. comments_create view 함수 정의
    
    ```python
    from .models import Article
    from .forms import ArticleForm, CommentForm
    
    def detail(request, pk):
        article = Article.objects.get(pk=pk)
        comment_form = CommentForm()
        context = {
            'article': article,
            'comment_form': comment_form,
        }
        return render(request, 'articles/detail.html', context)
    
    **def comments_create(request, pk):
        article = Article.objects.get(pk=pk)
        comment_form = CommentForm(request.POST)
        if comment_form.is_valid():
            comment_form.save()
            return redirect('articles:detail', article.pk)
        context = {
            'article': article,
            'comment_form': comment_form
        }**
        # redirect는 에러 정보를 전송할 수 없음
        **return render(request, 'articles/detail.html', context)**
    ```
    

1. 댓글 작성
    
    ![image.png](images/mto_1_7.png)
    
    **아까와 같은 에러 발생**
    
    - **외래 키 데이터를 넣는 타이밍이 필요함**
    - **외래 키를 넣으려면 2가지 조건이 필요**
        1.  comment 인스턴스 필요
        2. save 메서드가 호출되기 전이어야 함
    - **그러나 comment 인스턴스는 save 메서드가 호출되어야 생성됨**
    
    **`save(commit=False)`** : DB에 저장 요청을 보내지 않고 인스턴스만 반환
    

1. `save`의 `commit` 인자를 활용해 외래 키 데이터 추가 입력
    
    ```python
    # articles/views.py
    
    from .models import Article
    from .forms import ArticleForm, CommentForm
    
    def comments_create(request, pk):
        article = Article.objects.get(pk=pk)
        comment_form = CommentForm(request.POST)
        **if comment_form.is_valid():
            comment = comment_form.save(commit=False)
            comment.article = article
            comment.save()
            return redirect('articles:detail', article.pk)**
        context = {
            'article': article,
            'comment_form': comment_form
        }
        return render(request, 'articles/detail.html', context)
    ```
    

1. 결과 확인
    
    ![image.png](images/mto_1_8.png)
    

### 댓글 READ

- 페이지에서 댓글 출력
    
    ```python
    # articles/views.py
    from .models import Article
    from .forms import ArticleForm, CommentForm
    
    def detail(request, pk):
        article = Article.objects.get(pk=pk)
        comment_form = CommentForm()
        **comments = article.comment_set.all() # 해당 게시글에 작성된 모든 댓글 조회(역참조)
        context = {
            'article': article,
            'comment_form': comment_form,
            'comments': comments,
        }**
        return render(request, 'articles/detail.html', context)
    ```
    
    ```html
    <!-- articles/detail.html -->
    
    {% comment %} 댓글 출력 {% endcomment %}
    <h4>댓글 목록</h4>
    <ul>
      {% for comment in comments %}
        <li>{{ comment.content }}</li>
      {% endfor %}
    </ul>
    <hr>
    {% comment %} 댓글 작성 {% endcomment %}
    <form action="{% url "articles:comments_create" article.pk %}" method='POST'>
      {% csrf_token %}
      {{ comment_form }}
      <input type="submit">
    </form>
    ```
    
    ![image.png](images/mto_1_9.png)
    

### 댓글 DELETE

1. 댓글 삭제
    
    ```python
    # articles/urls.py
    
    from django.urls import path
    from . import views
    
    app_name = 'articles'
    urlpatterns = [
    		...
        path('<int:pk>/comments/', views.comments_create, name='comments_create'),
        **path('<int:article_pk>/comments/<int:comment_pk>/delete/', views.comments_delete, name='comments_delete'),**
    ]
    ```
    
    ```python
    # articles/views.py
    
    from .models import Article, Comment
    from .forms import ArticleForm, CommentForm
    
    def comments_delete(request, article_pk, comment_pk):
        comment = Comment.objects.get(pk=comment_pk)
        comment.delete()
        return redirect('articles:detail', article_pk)
    ```
    
    ```html
    <!-- articles/detail.html -->
    
    <hr>
      {% comment %} 댓글 출력 {% endcomment %}
      <h4>댓글 목록</h4>
      <ul>
        {% for comment in comments %}
          <li>{{ comment.content }}</li>
          **{% comment %} 댓글 삭제 {% endcomment %}
          <form action="{% url "articles:comments_delete" article.pk comment.pk %}">
            {% csrf_token %}
            <input type="submit" value='DELETE'>
          </form>**
        {% endfor %}
      </ul>
      <hr>
      {% comment %} 댓글 작성 {% endcomment %}
      <form action="{% url "articles:comments_create" article.pk %}" method='POST'>
        {% csrf_token %}
        {{ comment_form }}
        <input type="submit">
      </form>
      <hr>
    ```
    
    ![image.png](images/mto_1_10.png)
    

# 참고

## 데이터 무결성

- **데이터 베이스에 저장된 데이터의 정확성, 일관성, 유효성을 유지하는 것**
- **데이터 베이스에 저장된 데이터 값의 정확성을 보장하는 것**

**→ 중요성**

1. 데이터의 신뢰성 확보
2. 시스템 안정성
3. 보안 강화

## admin site 댓글 등록

`Comment` 모델을 admin site에 등록해 CRUD 동작 확인하기

```python
# articles/admin.py

from django.contrib import admin
from .models import Article, **Comment**

admin.site.register(Article)
**admin.site.register(Comment)**
```

## 댓글 추가 구현

```html
<!-- articles/detail.html -->

{% comment %} 댓글 출력 {% endcomment %}
<h4>댓글 목록</h4>
<p>{{ comments|length }}개의 댓글이 있습니다.</p>
<p>{{ article.comment_set.count }}개의 댓글이 있습니다 쿼리셋</p>
<ul>
  {% for comment in comments %}
    <li>{{ comment.content }}</li>
    {% comment %} 댓글 삭제 {% endcomment %}
    <form action="{% url "articles:comments_delete" article.pk comment.pk %}">
      {% csrf_token %}
      <input type="submit" value='DELETE'>
    </form>
  {% empty %}
    <p>댓글이 없어요</p>
  {% endfor %}
</ul>
```

### 1. 댓글이 없는 경우 대체 콘텐츠 출력

- **`for empty`**
    
    ```html
    {% for comment in comments %}
      <li>{{ comment.content }}</li>
      {% comment %} 댓글 삭제 {% endcomment %}
      <form action="{% url "articles:comments_delete" article.pk comment.pk %}">
        {% csrf_token %}
        <input type="submit" value='DELETE'>
      </form>
    **{% empty %}
      <p>댓글이 없어요</p>**
    {% endfor %}
    ```
    

### 2. 댓글 개수 출력하기

- **DTL filter - `length`**
    
    ```html
    <p>{{ comments|length }}개의 댓글이 있습니다.</p>
    ```
    
- **QuerySet API - `count()`**
    
    ```html
    <p>{{ article.comment_set.count }}개의 댓글이 있습니다 쿼리셋</p>
    ```
    

# 개인 메모

## 객체 출력하기

```python
# articles/models.py

from django.db import models

# Create your models here.
class Category(models.Model):
    name = models.CharField(max_length=20)
```

![image.png](images/mto_1_11.png)

### 이름으로 출력하기

```python
# articles/models.py

from django.db import models

class Category(models.Model):
    name = models.CharField(max_length=20)

    **def __str__(self):
        return self.name**
```

![image.png](images/mto_1_12.png)