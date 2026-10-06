# JDBC 고객·주문 관리

Java 콘솔 메뉴에서 Oracle DB의 고객을 조회·추가·수정·삭제하고 주문 목록을 확인하는 중간 과제.

## 구현한 부분

수업에서 만든 `Customer`·`Order` entity와 조회 화면을 사용하고, `MainController`의 메뉴를 switch 분기로 구성했다. 수정 입력을 받는 `UpdateCustomerView`, 삭제 확인과 관리자 비밀번호를 받는 `DeleteCustomerView`를 추가했다.

- **고객 수정**: ID로 고객을 조회하고 현재 정보를 표시한 다음, 입력한 이름·나이·등급·직업·적립금을 `UPDATE`한다. 수정 후 같은 ID를 다시 조회해 결과를 출력한다.
- **고객 삭제**: 대상 확인과 Y/N 입력을 거쳐 `DELETE`한다. 주문 참조 때문에 Oracle 오류 2292가 발생하면 관리자 비밀번호 확인 경로로 이동한다. 비밀번호는 코드에 고정된 과제용 값이다.
- **주문이 있는 고객 삭제**: `DeleteCustomerAll`이 auto-commit을 끄고 주문 → 고객 순서로 삭제한다. 두 작업이 끝나면 commit, SQL 오류가 나면 rollback하며 마지막에 auto-commit을 복구한다.
- **주문 조회**: 주문·고객·제품 테이블을 join하고 고객 이름·제품명·수량·배송지를 출력한다.

## 입력에서 DB까지

`Scanner` 메뉴 입력 → `MainController`의 switch → View 입력 → `PreparedStatement` SQL → View 결과 출력 순서다. SQL 실행은 Controller 안에 있으며 `findCustomerById`를 수정·삭제 경로에서 함께 사용한다.

| 위치 | 역할 |
|---|---|
| [MainController](src/mvc_jdbc_test/controller/MainController.java) | 메뉴 분기, 조회·CRUD, 삭제 트랜잭션 |
| [view](src/mvc_jdbc_test/view/) | 콘솔 목록·입력·확인 메시지 |
| [entity](src/mvc_jdbc_test/entity/) | 고객·주문 결과를 담는 Java 객체 |
| [JDBC_Connecter](src/jdbc_test/JDBC_Connecter.java) | Oracle driver와 Connection 생성 |

## 실행

IDE에서 이 폴더를 열고 `src/`를 source root로 지정한다. Oracle JDBC driver를 classpath에 추가하고, `JDBC_Connecter`의 `localhost:1521/xe`와 계정 설정에 맞는 DB를 준비한다. 프로그램은 `고객`·`주문`·`제품` 테이블을 사용한다. 테이블과 seed 데이터 SQL은 [0825.sql](../DB_2025_2/0825.sql)에 있다.

`mvc_jdbc_test.controller.MainController.main`을 실행한 뒤 1~5번 메뉴를 선택한다. 0번은 종료다. 공통 Maven/Gradle 빌드나 DB migration은 없다.
