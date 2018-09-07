# Function
---------------
### 호이스팅
> Hoisting : "끌어올리다"
- 변수 선언과 함수 선언을 끌어올림

~~~javascript
console.log(a());
// a()가 선언되지 않았지만 아래에 있는 a()의 선언을 호이스팅하여 에러가 발생하지 않음
console.log(b());
console.log(c());

function a(){
  return 'a';
}
var b = function bb(){
  return 'bb';
}
var c = function(){
  return 'c';
}
~~~
~~~javascript
// 실제 실행
function a(){
  return 'a';
}
var b;
var c;
console.log(a());
console.log(b());
console.log(c());

b = function bb(){
  return 'bb';
}
c = function(){
  return 'c';
}
~~~

### 함수 선언문과 함수 표현식
- 함수 선언문
~~~javascript
function a(){
  return 'a';
}
~~~
- 기명 함수 표현식
~~~javascript
var b = function bb(){
  return 'bb';
}
~~~
- (익명)함수표현
~~~javascript
var c = function(){
  return 'c';
}
~~~
- 함수 선언문은 선언과 할당 모두 hoisting된다.  
- 가독성 면에서도 좋지 않음
- 함수 표현식을 쓰도록 하자.


### 함수 스코프와 실행 컨텍스트
- 스코프 : 변수의 유효범위(변수)
- 실행 컨텍스트 : 실행되는 코드 덩어리(추상적 개념)
- 스코프는 함수가 정의될 때, 실행 컨텍스트는 함수가 실행될 때 생성된다.
- 실행 컨텍스트에는 호이스팅, this 바인딩 등의 정보가 담긴다.

### 메소드와 함수의 차이
- 메소드 : 함수처럼 생겼는데 앞에 . 이 붙어있는 애들
- 메소드는 this를 바인딩함.
  - bind는 ‘묶다, 결속시키다’ 라는 의미입니다.execution context가 생성될 때 자바스크립트 엔진은 해당 함수 또는 메소드를 실행시키기 위해 필요한 정보들, 즉 어떤 지역변수들이 선언되었는지, this에는 무엇이 담겨야 하는지 등의 정보들을 정하는 작업을 수행하는데, 이 때 this의 정보를 담는 과정을 흔히 ‘바인딩한다’라고 표현합니다. 여타의 언어들과 달리 자바스크립트는 new 연산자, 프로토타입 체이닝 혹은 call, apply 등에 의해 각 상황별로 실행되는 시점에 비로소 this에 대상이 연결되는 ‘동적’ 바인딩이 이뤄집니다. 함수 또는 메소드 내부에서 this를 어떤 것으로 인식할 것인지가 해당 함수 또는 메소드를 호출하는 시점에 결정된다고 이해하시면 되겠습니다.


### 콜백함수의 정의 및 특징
> "Something will call this function back"
- 제어권을 넘긴다.

~~~javascript
setInterval(function(){
  console.log('1초마다 실행될 것입니다.');
}, 1000);
// 인자 1(function~):콜백함수 -> 제어권을 setInterval()에 넘김  
// 인자 2 : 주기(ms)
~~~

- 콜백함수의 특징
  - 다른 함수(A) 매개변수로 콜백함수(B)를 전달하면, A가 B의 제어권을 갖게 된다.
  - 특별한 요청(bind)이 없는 한 A에 미리 정해진 방식에 따라 B를 호출한다.
  - 미리 정해진 방식이란 this에 무엇을 바인딩할 지, 매개변수에는 어떤 값들을 지정할지, 어떤 타이밍에 콜백을 호출할지 등이다.
  - 주의) 콜백은 메소드가 아닌 '함수'이다.
