# Rails Framework
--------------
### Framework
> 재사용이 가능한 클래스

- Framework vs. Library  
  - 라이브러리는 사용자 코드에서 호출되어야 한다.(사용자가 호출할 때 자신의 코드를 실행)
  - 프레임워크는 스스로 사용자 코드를 호출한다.(프레임워크가 사용자의 코드를 직접 지배함.)
  - 프로그램의 실행 주체가 역전됌(제어반전) : 프레임워크의 본질  
  - 레일즈는 프레임워크, gem은 라이브러리에 해당된다.


- Framework 사용의 장점
    1. 개발 생산성이 향상된다.
    2. 유지보수성이 뛰어나다.
    3. 최신 기술 트렌드에 대응하기 쉽다.
    4. 일정 이상의 품질을 기대할 수 있다.  


- Ruby언어는 Ruby on Rails 외에도 Sinatra, Ramaze 등의 프레임워크를 사용할 수 있다.  

### MVC패턴
> Ruby on Rails 외에 다른 Framework에서도 많이 사용되니 잘 이해해 놓는 것이 중요하다.

- M(Model)  
  - DataBase Management System (DB를 효율적으로 관리)  
  - Oracle : 많이 사용되는 DBMS중 하나 -> DBA, Database Administrator  
- V(View)  
  - 사용자와의 상호작용을 하는 영역
  - HTML(HyperText Markup Language), CSS, Javascript(동적 효과) -> 웹 퍼블리셔, 프론트엔드 개발자
  - 사용자가 브라우저를 통해 접속
- C(Controller)  
  - 기능 구현, 중간 관리자 역할
  - Ruby 등의 프로그래밍 언어로 구현
  - 서버 제공 -> 백엔드, 웹 개발자
