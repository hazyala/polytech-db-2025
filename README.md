# SQL 설계와 JDBC 고객 관리 실습

Oracle SQL 수업 기록, 온라인몰 DB 설계 산출물과 콘솔 고객 관리 중간 과제.

| 위치 | 읽을 내용 |
|---|---|
| `DB_2025_2/*.sql` | 날짜별 SQL 실습 |
| `DB_2025_2/`의 drawio XML·PNG | 온라인몰 개념·논리·테이블 설계 산출물 |
| [DataBase_Midterm-Exam_1109](DataBase_Midterm-Exam_1109/README.md) | 고객·주문 조회, 고객 추가·수정·삭제 |

중간 과제는 Java 콘솔 입력을 MainController의 switch로 분기해 JDBC 쿼리와 View에 연결한다. 메뉴 분기와 수정·삭제 View를 추가했고, 주문이 있는 고객을 삭제할 때 주문과 고객 삭제를 하나의 트랜잭션으로 묶었다. entity는 수업 코드를 사용했다.

실행은 하위 프로젝트의 IDE·Oracle 설정이 필요하다. root 공통 빌드나 REST API는 없고 SQL·설계 과제와 Java 실행 프로젝트를 구분해서 읽는다. [DB 설계](DB_2025_2/README.md)에는 한빛마트의 제조업체·회원·상품·주문·게시글 관계와 SQL이 있다.
