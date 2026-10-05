# JDBC 고객 관리 중간 과제

Scanner로 메뉴를 입력받아 고객·주문 조회와 고객 추가·수정·삭제를 처리한다.

## 과제 당시 기록

Main Controller에서 구조를 siwtch case문으로 변환하여 편리하게 고객 정보 조회, 수정, 삭제, 추가를 할 수 있도록 수정하였습니다. MainController의 하단부에 //===================================== 중간 과제 ============================================ 로 적혀있는 구간부터 새로 수행한 내용입니다.
entity는 수업내용때 제작 한 내용 그대로 사용하였습니다.
view는 DeleteCustomerVirew 와 UpDateCustomerView 클래스만 추가로 제작하여 수행하였습니다.


## 현재 코드 경로

`mvc_jdbc_test.controller.MainController`가 switch 분기와 SQL 실행을 맡고, `entity/`는 Customer·Order, `view/`는 콘솔 표시와 입력을 처리한다. `jdbc_test.JDBC_Connecter`가 Oracle driver를 로드하고 localhost:1521/xe에 연결한다. DAO 계층이 별도로 있다고 가정하지 않는다.

IDE에서 이 폴더를 Java 프로젝트로 열고 src를 source root로 지정한다. Oracle JDBC driver와 코드 상수에 맞는 DB 계정·customer/orders 테이블이 필요하다. 전체 테이블을 자동 생성하는 migration이나 공통 Maven/Gradle 빌드는 없다. 준비 후 `mvc_jdbc_test.controller.MainController.main`을 실행한다.

DB 없이 독립 실행되는 프로그램은 아니다. 이 README 정비에서는 연결 값·SQL·entity를 변경하지 않았다.
