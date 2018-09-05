# Scaffolding
--------------

> Rails가 제공하는 기능 중 하나로, 쉽게 CRUD(Create-Read-Update-Delete)기능을 가진 애플리케이션을 만들 수 있게 하는 기능.  
view, controller, routing, model 모두 생성됨.  

### Scaffolding의 필요성
- 일단 동작하는 애플리케이션을 만들고 싶을 때
- 데이터 유지 관리 등의 레이아웃을 열심히 만들 필요가 없는 페이지를 대량으로 만들어야 할 때
- Rails의 기본적인 CRUD 구현을 이해하고 싶을 때

### 스캐폴딩 기능(생성)
~~~
rails generate scaffold name field:type [...] [options]  
rails g scaffold book isbn:string title:string price:integer publish:string  
-------------------------------------------------------  
name : 모델 이름
field : 필드 이름
type : 자료형
options : 동작 옵션
~~~

### css 수정
- bootstrap cdn
- assets/stylesheets/scaffolds.scss

### 자동 생성된 라우트 확인- resources 메서드
- 스캐폴딩 기능으로 애플리케이션을 생성하면 config/routes.rb에 다음과 같은 코드가 추가된다.  
- resources메서드로 books라는 리소스의 표준적인 라우트가 정의됨.

~~~
/// routes.rb
Rails.application.routes.draw do
  resources :books
end
~~~

### 뷰 헬퍼(View Helper)
> 뷰 헬퍼는 템플릿 파일을 작성할 때 도움을 주는 메서드를 의미한다. 뷰 헬퍼를 사용하면 입력 양식 요소 생성을 비롯해 문자열 또는 숫자 정형화, 인코딩 처리 등 뷰에서 자주 사용되는 처리를 손쉽게 해낼 수 있다.

ex) link_to 메서드

> index.html.erb

~~~
link_to(body, url[, html_options])
--------------------------------------------------------
body : 링크 텍스트
url : 링크 대상 경로(또는 매개 변수 정보)
html_options : <a>태그에 적용할 옵션 정보("<속성 이름>:<값>"의 해시 형태)
~~~


### before_action 메서드
> books controller

~~~
before_action method, only: action
--------------------------------------------------------
method: 필터로 실행되는 메서드
action: 필터를 적용할 액션 메서드(배열)
~~~

### 부분템플릿
> books/new.html.erb
- 메인 템플릿에서 부분 템플릿을 불러들일 때 render를 사용
- 메인 템플릿에서는 별도로 사용하는 부분만 입력

~~~
부분템플릿 : _[이름].html.erb
~~~
~~~
<%= render 'form' %>
# _form.html.erb를 부분템플릿으로 사용하겠다는 의미
~~~

### routing
~~~
rake routes
# 생성된 route 들을 확인할 수 있음
~~~
- prefix : uri와 path가 생성됨   
- URI Pattern : routes.rb에 직접 생성시킨 패턴  

~~~
redirect_to '/books'      # prefix
redirect_to books_url     # URI pattern
~~~
