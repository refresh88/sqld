# 제2장 SQL 활용

---

[틀린문제](https://www.notion.so/eef3a04dc6904a7fa04367a0b4214437?pvs=21)

- 오라클 + 조인은 +가 없는 쪽으로 outer join을 함.
    
    ```java
    from team A, member B
    where A.name = B.name(+)
    
    // ANSI
    from team A left outer join member B
    ON(A.name = B.name)
    ```
    

- 오라클 계층형 쿼리
    - START WITH 절은 계층 구조의 시작점을 정하는 구문
    - ORDER SIBLINGS BY 절은 형제 노드 사이에서 정렬을 지정하는 구문이다.
    - 순방향전개란 부모 노드로부터 자식 노드 방향으로 전개하는 것을 말한다.
    - 루트 노드의 LEVEL 값은 1이다.
    - PRIOR 키워드는 SELECT, WHERE 절에서도 사용 가능(CONNECT BY에서만 쓸수있는게 아님)

- 서브쿼리
    - 다중 행 서브쿼리 비교 연산자는 단일 행 서브쿼리의 비교 연산자로도 사용할 수 있다.
    - 서브쿼리는 단일 행 또는 복수 행 비교 연산자와 함께 사용할 수 있다.
    - 서브쿼리는 SELECT, FROM, HAVING, ORDER BY절 등에서 사용이 가능하다.
    - 연관 서브쿼리는 서브쿼리가 메인쿼리 컬럼을 포함하고 있는 형태의 서브쿼리이다.

- CUBE, GROUPING SETS, ROLLUP 세가지 그룹 함수 모두 일반 그룹 함수로 동일한 결과를
추출할 수 있다.
- 함수의 인자로 주어진 컬럼의 순서에 따라 다른 결과를 추출하게 되는 그룹 함수는 ROLLUP 이며, 나열된 컬럼에 대해 계층 구조로 집계를 출력한다.
- CUBE, ROLLUP, GROUPING SETS 함수들에 의해 집계된 레코드에서 집계 대상 컬럼 이외의
GROUP 대상 컬럼의 값은 NULL을 반환한다.
- CUBE 그룹 함수는 인자로 주어진 컬럼의 결합 가능한 모든 조합에 대해서 집계를 수행하므로 다른 그룹 함수에 비해 시스템에 대한 부하가 크다.

- `RANK` WINDOW FUNCTION은 동일 값에 대해서는 동일 순위를 부여하고 중간 순위는 비워 두지만, `DENSE_RANK` 함수는 동일 순위를 부여하되 중간 순위를 비우지 않는다. `ROW_NUMBER` 함수는동일 값에 대해서도 유일한 순위를 부여한다.