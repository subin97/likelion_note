# this
----------
### 상황별로 달라지는 this와 명시적인 this 바인딩 방법
- 전역공간에서 객체 : window, global
- 함수 내부에서의 객체(default) : window, global
- 메소드 호출 시의 객체 : 메소드 호출 주체(메소드 명 바로 앞)  
  - 함수는 (전역객체의) 메소드다(라고 생각하자!)

~~~javascript
var a={
  b: function(){
    console.log(this);
  }
}
a.b();  // this : a
~~~

~~~javascript
var a = {
  b: {
    c: function(){
      console.log(this);
    }
  }
}
a.b.c();  // this : a,b
~~~

- callback에서의 객체
  - 기본적으로는 함수의 this와 같다.
  - 제어권을 가진 함수가 callback의 this를 명시한 경우 그에 따른다.
  - 개발자가 this를 바인딩한 채로 callback을 넘기면 그에 따른다.

- 생성자 함수에서의 객체 : 인스턴스
