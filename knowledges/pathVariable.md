(4/25 10줄 글쓰기)
PathVariable & Query Parameter

### PathVariable과 Query Parameter는 무엇일까?

#### 1. Query Parameter

페이지를 만들 때 페이지마다 식별된 파라미터 경로가 필요하다.  
다음과 같이 get 파라미터를 사용하여 데이터를 넘길 수 있다.  
  
> /users?id=123    # 아이디가 123인 사용자를 가져온다.
  
서버로 부터 id변수를 얻을 수 있다.


#### 2. Path Variable  
  
데이터를 넘기는 다른 방법 중 하나로 Path Variable이 있다.

> /users/123       # 아이디가 123인 사용자를 가져온다.

123을  서버로 전달한다.  
**경로를 변수로** 사용할 수 있다.  

#### 3. Path Variable & Query Parameter는 언제 사용하는가!

resource를 식별하고 싶으면 Path Variable  
정렬이나 필터링을 한다면 Query Parameter를 사용하는 것이 BestPractice이다.

> /users	# 사용자 목록을 가져온다.
> /users?occupation=programmer # 프로그래머인 사용자 목록을 가져온다.
> /users/123	# 아이디가 123인 사용자를 가져온다.
  
또한 기본적인 CRUD 기능을 위해서 query parameter를 정의할 필요는 없다.  
대신 원하는 기능에 맞게 HTTP 메소드를 바꾸어야 한다.  

> /users [GET] # 사용자 목록을 가져온다.
> /users [POST] # 새로운 사용자를 생성한다.
> /users/123 [PUT] # 사용자를 갱신한다.
> /users/123 [DELETE] # 사용자를 삭제한다.

#### 4. 정리

위의 방법대로 하지 않아도 API를 만들 수 있으나  
다른 개발자들과의 협업과 개발 효율을 고려하면 BestPractice를 따르는게 좋다!



[출처](https://ryan-han.com/post/translated/pathvariable_queryparam/)
