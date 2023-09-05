# 제1장 SQL 기본

---

[틀린문제](https://www.notion.so/dceb11021dc240c79fff75b8598962ea?pvs=21)

- SQL 문장 종류
    - DML (데이터 조작어)
        - SELECT
        - INSERT
        - UPDATE
        - DELETE
    - DDL(데이터 정의어)
        - CREATE
        - ALTER
        - DROP
        - RENAME
    - DCL(데이터 제어어)
        - GRANT
        - REVOKE
    - TCL(트랜젝션 제어어)
        - COMMIT
        - ROLLBACK

- DML명령어들을 호스트 프로그램 속에 삽입되어 사용되는 데이터 부속어(Data Sub Language)
라고도 한다.

- UNIQUE는 테이블 내에 중복값이 있으면 안되지만, NULL은 가능하다.

- 특정 컬럼 삭제
    - ALTER TABLE 테이블명 DROP COLUMN 컬럼명

- 테이블명 바꾸기(ANSI 표준)
    - RENAME 이전테이블명 TO 바꿀테이블명;

- Delete Action
    1. Cascade ： Master 삭제 시 Child 같이 삭제
    2. Set Null ： Master 삭제 시 Child 해당 필드 Null
    3. Set Default : Master 삭•제 시 Child 해당 필드 Default 값으로 설정
    4. Restrict : Child 테이블에 PK 값이 없는 경우만 Master 삭제 허용
    5. No Action : 참조무결성을 위반하는 삭제/수정 액션을 취하지 않음
    
- Insert Action
    1. Automatic : Master 테이블에 PK가 없는 경우 Master PK를 생성 후 Child 입력
    2. Set Null : Master 테이블에 PK가 없는 경우 Child 외부키를 Null 값으로 처리
    3. Set Default : Master 테이블에 PK가 없는 경우 Child 외부키를 지정된 기본값으로 입력
    4. Dependent ： Master 테이블에 PK가 존재할 때만 Child 입력 허용
    5. No Action : 참조무결성을 위반하는 입력 액션을 취하지 않음

- TRUNCATE TABLE과 DROP TABLE은 로그를 남기지 않는다.

- `DROP TABLE`은 **테이블의 데이터를 모두 삭제하고 디스크 사용량도 없앨（초기화） 수 있지만, 테이블의 스키마 정의도 함께 삭제된다.**
- 특정 테이블의 **모든 데이터를 삭제하고, 디스크 사용량을 초기화** 하기위해서는 
`TRUNCATE TABLE` 명령을 사용하여야 한다.
- `DELETE TABLE`은 테이블의 **데이터를 모두 삭제하지만, 디스크 사용량을 초기화 하지는 않는다**.
- 뭔가 좀 다 지우는 순서를 보면
    - DROP > TRUNCATE > DELETE

![Untitled](%E1%84%8C%E1%85%A61%E1%84%8C%E1%85%A1%E1%86%BC%20SQL%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%2013713c02f62a4d969155bfadd5b8c496/Untitled.png)

- NULL값이 포함된 사칙연산은 모두  NULL이다.

- 오라클은 공백을 NULL로 인식한다.
- SQL Server는 공백을 공백으로 인식한다.

- count(*)는 null도 카운트 함.

- NULL 비교는 오직 ‘IS NULL’, ‘IS NOT NULL’만 가능

- GROUP BY로 그룹핑된 컬럼에 대해서 HAVING 조건절을 사용할 경우 집계된 컬럼의 FILTRER조건으로 사용할 수가 있다. 이런 경우 HAVING 절에 집계함수가 없이도 사용할 수 있다.
    
    ```java
    select menu_id, code, count(*) as cnt
    from system_record
    where use_date between sysdate - 1 and sysdate
    group by menu_id, code
    having menu_id = 3 and code = 100;
    ```
    

- select 문장 실행 순서
    - FROM - WHERE -GROUP BY - HAVING - SELECT - ORDER BY

-