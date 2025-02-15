## 테스트코드 컨벤션
테스트코드는 특정 기능을 테스트하는 용도지만  
특정 코드가 어떤일을 하는지 가장 빠르게 볼 수 있는 코드기도 하다  
이 컨벤션에는 정답이 없지만 가능한 가독성을 높이도록 한다.  

## 기본적인 규칙
Given-When-Then 에 맞춰서 작성한다.

## 레이어 별 규칙

### 레포지토리 테스트 코드
메서드 명 : givenTestData_when{CRUD}_thenWorksFine  
CRUD는 inserting, searching과 같은것을 의미한다.  
- ex) givenTestData_whenInserting_thenWorksFine
  
worksFine은 정상적으로 작동하는 경우에 붙여주며  
만약 예외를 발생하면 케이스면 thenThrowsException으로 작성한다.  
- ex) givenTestData_whenSearching_thenThrowsEntityNotFoundException
  

### 서비스(비즈니스 로직) 테스트 코드
메서드 명 : given{Parameter}_when{Acting}_thenReturns{Entity}  
파라미터가 유효하지 않다면 givenNonExistentParameter로 작성한다  
- ex) givenNonExistentUserId_whenGetUser_thenReturnsUser
  
만약 예외를 발생시킨다면  
- ex) givenNonExistentArticle_whenGetArticle_thenThrowsEntityNotFoundException
  

### 컨트롤러 테스트 코드
메서드 명 : given{Parameter}_when{Acting}_thenReturns  
만약 400번대나 500번대 상태코드를 갖는 오류라면  
thenThrows{Status}Error로 작성한다  
- ex) givenNonExistentUserId_whenGetUser_then404NotFoundError
  
컨트롤러 테스트 코드이므로 에러코드를 넣어주는것이 더 직관적이라고 생각한다.  

