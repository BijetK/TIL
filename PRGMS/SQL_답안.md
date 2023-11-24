# 



### Q2

- 문제 이름 

  : 재구매가 일어난 상품과 회원 리스트 구하기

- 문제 설명

  : 다음은 어느 의류 쇼핑몰의 온라인 상품 판매 정보를 담은 `ONLINE_SALE` 테이블 입니다. `ONLINE_SALE` 테이블은 아래와 같은 구조로 되어있으며 `ONLINE_SALE_ID`, `USER_ID`, `PRODUCT_ID`, `SALES_AMOUNT`, `SALES_DATE`는 각각 온라인 상품 판매 ID, 회원 ID, 상품 ID, 판매량, 판매일을 나타냅니다.

  | Column name    | Type    | Nullable |
  | -------------- | ------- | -------- |
  | ONLINE_SALE_ID | INTEGER | FALSE    |
  | USER_ID        | INTEGER | FALSE    |
  | PRODUCT_ID     | INTEGER | FALSE    |
  | SALES_AMOUNT   | INTEGER | FALSE    |
  | SALES_DATE     | DATE    | FALSE    |

- 문제

  : `ONLINE_SALE` 테이블에서 동일한 회원이 동일한 상품을 재구매한 데이터를 구하여, 재구매한 회원 ID와 재구매한 상품 ID를 출력하는 SQL문을 작성해주세요. 결과는 회원 ID를 기준으로 오름차순 정렬해주시고 회원 ID가 같다면 상품 ID를 기준으로 내림차순 정렬해주세요.

- 문제 분석

  1. 동일한 회원이 동일한 상품을 재구매,
  2. 재구매한 `회원 ID`와 `상품 ID`를 출력
  3. 회원 ID `오름차순`
  4. 회원 ID가 같다면 상품 ID 기준 `내림차순`

- 답안제출

  ```sql
  SELECT USER_ID, PRODUCT_ID
  FROM ONLINE_SALE
  GROUP BY USER_ID, PRODUCT_ID
  HAVING COUNT(PRODUCT_ID) > 1
  ORDER BY USER_ID ASC, PRODUCT_ID DESC
  ```



### Q3

- 답안제출

  ```sql
  WITH A AS (
  SELECT DATE_FORMAT(SALES_DATE, '%Y-%m-%d') as SALES_DATE, PRODUCT_ID, USER_ID, SALES_AMOUNT
  FROM ONLINE_SALE
  WHERE DATE_FORMAT(SALES_DATE, '%Y-%m') = "2022-03"
  UNION ALL
  SELECT DATE_FORMAT(SALES_DATE, '%Y-%m-%d') as SALES_DATE, PRODUCT_ID, NULL AS USER_ID, SALES_AMOUNT
  FROM OFFLINE_SALE
  WHERE DATE_FORMAT(SALES_DATE, '%Y-%m') = "2022-03"
  )
  
  SELECT *
  FROM A
  ORDER BY SALES_DATE ASC, PRODUCT_ID ASC, USER_ID ASC
  ```

  

### Q4

- 문제 이름

  : 아픈 동물 찾기

- 문제 설명

  : `ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

  | NAME             | TYPE       | NULLABLE |
  | ---------------- | ---------- | -------- |
  | ANIMAL_ID        | VARCHAR(N) | FALSE    |
  | ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
  | DATETIME         | DATETIME   | FALSE    |
  | INTAKE_CONDITION | VARCHAR(N) | FALSE    |
  | NAME             | VARCHAR(N) | TRUE     |
  | SEX_UPON_INTAKE  | VARCHAR(N) | FALSE    |

- 문제

  : 동물 보호소에 들어온 동물 중 아픈 동물의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

- 문제 분석

  1. 아픈 동물 : INTAKE_CONDITION = 'Sick'
  2. 아이디 순으로 조회

- 답안 제출

  ```sql
  SELECT ANIMAL_ID, NAME
  FROM ANIMAL_INS
  WHERE INTAKE_CONDITION = 'Sick'
  ORDER BY ANIMAL_ID
  ```

  