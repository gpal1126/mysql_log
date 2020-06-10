## Query 작성

### * INSERT : 추가
- INSERT INTO USER_TB( email, password, name, reg_date) VALUES('이메일', '패스워드', '이름', NOW() );  
    - user_id 인덱스 값은 자동증가로 생략 가능하다.   
```
mysql > INSERT INTO USER_TB( email, password, name, reg_date) VALUES('이메일', '패스워드', '이름', NOW() );
```

​
### * UPDATE : 수정
- UPDATE USER_TB SET name='변경된 이름' WHERE user_id=1;  
```
mysql > UPDATE USER_TB SET name='변경된 이름' WHERE user_id=1;
```

​### * DELETE : 삭제
- 전체  row  삭제하기  
    - DELETE FROM USER_TB;
```
mysql > DELETE FROM USER_TB;
```
- 특정  row  삭제하기 : where 조건을 붙여 주면 된다.  
    - DELETE FROM USER_TB WHERE user_id=1;  
```
mysql > DELETE FROM USER_TB WHERE user_id=1;
```
- 하지만 실무에선 delete문 사용을 최소화한다. 
    모든 데이터의 로그를 남기기 위해 delete 대신 delete 관련 컬럼을 만들어 update 를 주로 한다!

​
### * SELECT : 조회
- 모든 row 값 조회 : *  
    - SELECT * FROM USER_TB;  
```
mysql > SELECT * FROM USER_TB;
```

- 특정 row  값 조회 : 컬럼이름  
    - SELECT user_id, email, name FROM USER_TB;  
```
mysql > SELECT user_id, email, name FROM USER_TB;
```

### ORDER BY : 정렬
- ASC : 오름차순(작은 값 -> 큰 값), 기본 값, 생략 가능  
    - SELECT * from USER_TB ORDER BY user_id ASC;  
```
mysql > SELECT * FROM USER_TB ORDER BY user_id ASC;
```

- DESC : 내림차순(큰 값 -> 작은 값)  
    - SELECT * from USER_TB ORDER BY user_id DESC;  
```
mysql > SELECT * FROM USER_TB ORDER BY user_id DESC;
```

### COUNT(*) : row 수
- SELECT COUNT(*) USER_TB;  
```
mysql > SELECT COUNT(*) FROM USER_TB;
```