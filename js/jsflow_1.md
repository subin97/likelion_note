# 데이터 타입
-----------------
### 기본형과 참조형의 차이가 생기는 이유
- Primitive type : 값을 그대로 할당
  - Number
  - String
  - Boolean
  - null
  - undefined
- Reference type : 값이 저장된 주소값을 할당(참조)
  - Object
    - Array
    - Function
    - RegExp
- 선언 과정에는 차이가 없으나, 기본형의 경우 값이 바뀌면 같았던 두 변수가 달라짐.
- 참조형의 경우 값이 바뀌어도 참조하는 변수가 같으면 두 변수는 같은 값을 참조함.
