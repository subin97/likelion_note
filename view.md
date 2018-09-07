# 뷰 개발
------------
### 입력 양식 생성 기초
> form_for와 form_tag 메서드는 모두 <form>태그를 생성하기 위한 메서드이다. 하지만 form_for은 특정 모델 객체를 처리할 때 특화된 메서드, form_tag는 모델과 관계 없는, 범용적인 입력 양식을 생성할 때 사용하는 메서드라는 차이점이 있다.  

- form_tag : 범용적인 입력 양식 생성
  - FormTag 헬퍼
  - Form 헬퍼
- form_for : 특정 모델에 특화된 입력 양식 생성
  - FormTag 헬퍼
  - f.Form 헬퍼

### `<form>`태그 대신 `<%= form_tag %>`
> 특정한 모델 편집이 목적이 아닌 범용적인 입력 양식을 생성할 때.   

~~~
<%= form_tag("URL", method: "post/get") do %>
  .....body.....
<% end %>
---------------------------------------------------------
 URL : 정보를 보낼 주소
 method : 방법(get/post)
 body : 입력 양식 내용
~~~
~~~
/// 예시

<form method="post" action = "/posts/create">
<%= form_tag("/posts/create", method: "post") do %>
~~~
위의 두 가지 태그는 같은 의미를 나타낸다.

- form_tag는 자동으로 보안 문제를 해결해준다.
  - 개발자도구에서 확인하면 쓰지 않은 hidden tag가 있음
  - html <form>태그를 사용할 때는 post 방식을 사용할 때 application controller에 있는 한 줄을 주석처리하고 사용하였다.
  - form_tag를 쓰면 토큰 input를 자동생성해줘서 문제를 해결해준다.

### `<%= form_for %>`태그
- 모델과 연동이 되는 form 태그로 수정에 용이하다.

 ~~~
<%= form_for @post, url: post_create_path, method: "post" do |f| %>
  <%= f.text_field :title %>
  <%= f.text_field :content %>
  <%= f.submit %>
<% end %>
 ~~~
 - 보통은 컨트롤러/액션에서 변수로 테이블의 row값을 선언해준다. 즉, @post = Post.new 또는 Post.find(params[:id])
 - 각 input이 Posts 테이블의 어떤 column값에 해당하는지 :column이름으로 써준다.
- form_for로 보낸 값은 적용된 모델 이름의 hash안에 담겨서 보내진다.
