## 테이블 관련 구문


### * 테이블 생성
```
CREATE TABLE USER_TB(    
    user_id int(11) unsigned NOT NULL AUTO_INCREMENT,
    email varchar(40) NOT NULL,
    password varchar(100) NOT NULL,
    name varchar(40),
    reg_date datetime,
    deleted int(11) unsigned DEFAULT 0,
    del_date datetime,
    PRIMARYKEY(user_id)
);
```

- unsigned : 양의 정수, int의 범위 : -2,147,483,648 ~ 2,147,438,647 이므로 음수를 사용하지 않을 때는 unsigned 설정  
- NOT NULL : NULL 허용 하지 않음, 기본 NULL  
- AUTO_INCREMENT : 자동 증가  
- DEFAULT : insert시 기본 값 설정  
- PRIMARYKEY(컬럼명) : 컬럼 기본키 설정  
- int(크기) : 정수형, 크기 기본 11  
- varchar(크기) : 문자형  
- datetime : 날짜와 시간  
- text : 긴 문자열  

​
### * 테이블 구조 조회
- DESC USER_TB;  
```
mysql > DESC USER_TB;
```

### * 테이블 이름 변경
- ALTER TABLE 기존 테이블명 RENAME 새 테이블명;  
```
mysql > ALTER TABLE USER_TB RENAME USER;
```

### * 테이블 삭제  
- DROP TABLE 테이블명;  
```
mysql > DROP TABLE USER_TB;
```

### * 테이블 컬럼 추가
- ALTER TABLE 테이블명 ADD 추가할컬럼명 타입 AFTER 컬럼명  
```
mysql > ALTER TABLE USER_TB ADD introduce varchar(500) AFTER name;
```

### * 테이블 컬럼 순서 변경
- ALTER TABLE 테이블명 MODIFY COLUMN 컬럼명 자료형 AFTER 다른컬럼;  
```
mysql > ALTER TABLE USER_TB MODIFY COLUMN introduce varchar(500) AFTER name;
```

### * 테이블 기존 컬럼 이름과 타입 변경  
- ALTER TABLE 테이블명 CHANGE 기존컬럼명 새로운컬럼명 타입;  
```
mysql > ALTER TABLE USER_TB CHANGE introduce intro text;
```

### * 테이블 컬럼 타입 변경  
- ALTER TABLE 테이블명 MODIFY 기존컬럼명 새로운 타입;  
```
mysql > ALTER TABLE USER_TB MODIFY name varchar(50);
```
​