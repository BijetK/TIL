# MySQL

## Python - MySQL

### 기본

```python
!pip install pymysql > /dev/null		#pymysql 설치

from google.colab import files			#mysql.json 파일
uploaded = files.upload()
filename = list(uploaded.keys())[0]
```

```python
import json
with open(filename) as fp:
    config_str = fp.read()
config = json.loads(config_str)
```

```python
import pymysql
conn = pymysql.connect(
    host = config['host'],
    user = config['user'],
    password = config['password'],
    database = config['database'],
    port = config['port']
)
```

### 테이블 생성

```python
cur = conn.cursor()
sql_create_table = '''
    create table if not exists users ( 
        uid varchar(20) not null primary key, 
        pwd char(44) not null, 
        uname varchar(20) not null,
        email varchar(40), 
        reg_date datetime default current_timestamp, 
        is_deleted int default 0 
    );
'''

cur.execute(sql_create_table)
```

![make_table](/md-images/make_table.jpg)

### 데이터 추가(Insert)

```python
cur = conn.cursor() 
sql_insert = "INSERT INTO users(uid, pwd, uname) VALUES('admin', '1234', '관리자');"
cur.execute(sql_insert)
sql_select = 'select * from users;'         
# 아직까진 hideisql에서는 확인 못함, 현재 cache 메모리에만 저장되어 있음. 
# 데이터를 디스크에 써야함 -> conn.commit()
cur.execute(sql_select)
row = cur.fetchone()
```

```python
row

=> ('admin', '1234', '관리자', None, datetime.datetime(2021, 8, 25, 13, 29, 49), 0)
```

```python
# 데이터를 하드 디스크에 쓰게 하는 명령
conn.commit()
```

- 여러건의 데이터 추가

  ```python
  sql_multi_insert = """
          INSERT INTO users(uid, pwd, uname) VALUES
              ('eskim', '1234', '김은숙'), ('wjlee', '1234', '이우정');
  """
  cur.execute(sql_multi_insert)
  conn.commit()
  ```

- Placeholder

  ```python
  sql_insert_ph = "INSERT INTO users(uid, pwd, uname) VALUES(%s, '1234', %s)"
  uid, uname = 'djy', '대조영'
  cur.execute(sql_insert_ph, (uid, uname))
  conn.commit()

- 여러개의 데이터를 placeholder를 이용해서 insert

  ```python
  users = (('gdhong', '홍길동'), ('jbpark', '박재범'))
  cur.executemany(sql_insert_ph, users)
  conn.commit()
  ```

  or

  ```python
  # for 반복문을 이용해서 insert 하기 (강사가 추천하는 방법)
  users = (('gdhong2', '홍길동'), ('jbplark2', '박재범'))
  for user in users:
      cur.execute(sql_insert_ph, user)
  conn.commit()
  ```



- 마무리

  ```python
  cur.close()
  conn.close()
  ```

### 데이터 조회(Select)

```python
sql_select = '''
        SELECT uid, uname, email, DATE_FORMAT(reg_date, '%Y-%m-%d %H:%i') AS reg_date
            FROM users
            WHERE is_deleted = 0
            ORDER BY reg_date;
'''
```

- 1건 조회

  ```python
  cur = conn.cursor()
  cur.execute(sql_select)
  row = cur.fetchone()         # fetchone
  row
  
  => ('admin', '관리자', None, '2021-08-25 13:29')
  ```

  ```python
  # 다음 줄 조회
  row = cur.fetchone()        # 다음게 나옴.
  row
  
  => ('eskim', '김은숙', None, '2021-08-25 13:37')
  ```

- 여러건 조회

  ```python
  cur = conn.cursor()
  cur.execute(sql_select)
  rows = cur.fetchmany(3)         # fetchmany
  rows
  
  =>
  (('admin', '관리자', None, '2021-08-25 13:29'),
   ('eskim', '김은숙', None, '2021-08-25 13:37'),
   ('wjlee', '이우정', None, '2021-08-25 13:37'))
  ```

- 모두 조회

  ```python
  cur = conn.cursor()
  cur.execute(sql_select)
  rows = cur.fetchall()         # fetchall
  rows
  
  =>
  (('admin', '관리자', None, '2021-08-25 13:29'),
   ('eskim', '김은숙', None, '2021-08-25 13:37'),
   ('wjlee', '이우정', None, '2021-08-25 13:37'),
   ('djy', '대조영', None, '2021-08-25 13:45'),
   ('gdhong', '홍길동', None, '2021-08-25 14:05'),
   ('jbpark', '박재범', None, '2021-08-25 14:05'))
  ```

  
