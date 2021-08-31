# MYSQL

## 데이터 조작

### SELECT

```mysql
SELECT (DISTINCT) field1, ... , fieldn, 함수
  FROM 'table명'
  WHERE '조건'
  JOIN '합칠 table명'
  ON 'join의 조건'
  GROUP BY 'field명'
  HAVING 'group by의 조건'
  ORDER BY 'field명, ....' (DESC)
  LIMIT '출력할 개수' OFFSET '몇번째 부터';
  

```

```mysql
EX) 아시아 대륙에서 인구가 가장 많은 도시 10개를 내림차순으로 보여줄 것 (대륙명, 국가명, 도시명, 인구수)

SELECT r.continent AS '대륙명', r.name AS '국가명',
 l.name AS '도시명', l.population AS '인구수'
 FROM city AS l
 JOIN country AS r
 ON l.countrycode = r.code
 WHERE r.continent = 'Asia'
 ORDER BY l.Population desc
 LIMIT 10;
```

### UPDATE (데이터 갱신)

```mysql
UPDATE 'table명' SET '바꿔야 하는 조건'
  WHERE '바뀌어야 하는 조건'

UPDATE city SET district = '경기'
  WHERE district = 'kyonggi';

=> district가 'kyonggi'인 것을 전부 '경기'로 바꿈
```

### INSERT (데이터 삽입)

```mysql
INSERT INTO 'table명' (column1, column2, ... , column n)
  VALUES (값1, 값2, ... , 값 n)
         (값i, 값ii, ... , 값 nn);			# 한번에 여러개 insert 가능
  
- auto_increase 일 때는 DEFAULT를 값으로 넣어준다.
- 모든 column을 다 쓸 때는 (column1, ...) 부분 생략 가능

EX)
insert into city (name, countrycode, district, population)
values ('Hwasong', 'KOR', 'Kyonggi', 312345);
```

### DELETE (데이터 삭제)

```mysql
DELETE FROM 'table명' WHERE '지울 조건'
```

### VIEW (뷰)

```mysql
CREATE VIEW LargeCity AS SELECT * FROM city WHERE population>7000000 with check option;

- table : 물리적 공간 O
- view : 물리적 공간 X 인 가상의 table. SHOW TABLES; 에서 나옴
```

### 날짜 형식

```mysql
DATE_FORMAT(dt, '%Y-%m-%d');	=> 2021-08-24
DATE_FORMAT(dt, '%h:%i:%s %p');	=> 03:01:53 PM		# %H 는 24시간 단위로 표시됨
DATE_FORMAT(dt, '%r');			=> 03:01:53 PM

NOW() = 2021-08-24 03:01:53
CURDATE() = 2021-08-24
CURTIME() = 03:01:53

SELECT DATE_ADD(CURDATE(), INTERVAL 5 DAY);	=> 2021-08-29	# 5일 뒤
SELECT TO_DAYS(CURDATE())					=> 738391		# 서기 0년 1월 1일부터 오늘이 몇일째인지
SELECT DAYOFWEEK(dt) FROM date_table;		=> data_table에 있는 날짜들의 요일 (1 : 일요일, 2: 월요일, ...)
```

