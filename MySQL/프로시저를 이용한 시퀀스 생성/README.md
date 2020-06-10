## 프로시저를 이용한 시퀀스 생성

### * 시퀀스 테이블 생성
```
CREATE TABLE sequences ( name varchar(32), currval BIGINT UNSIGNED ) ENGINE=InnoDB;
```
  
​  
### * 시퀀스 프로시저 생성
```
DELIMITER $$
CREATE PROCEDURE `create_sequence`(IN the_name text)
MODIFIES SQL DATA
DETERMINISTIC
BEGIN
    DELETE FROM sequences WHERE name=the_name;
    INSERT INTO sequences VALUES (the_name, 0);
END
```
  
​  
### * 시퀀스 function 생성
```
DELIMITER $$ 
CREATE FUNCTION `nextval`(the_name varchar(32))
RETURNS BIGINT UNSIGNED
MODIFIES SQL DATA
DETERMINISTIC
BEGIN
    DECLARE ret BIGINT UNSIGNED;
    UPDATE sequences SET currval=currval+1 WHERE name=the_name;
    SELECT currval INTO ret FROM sequences WHERE name=the_name limit 1;
    RETURN ret;
END
```
  
​  
### * 시퀀스 생성
```
INSERT INTO sequences VALUES ('test_seq', 0);
```
  
​  
### * 시퀀스 조회
```
select nextval('test_seq')
```
  
​  
### * 프로시저 조회 및 삭제
```
show procedure status;
drop procedure create_sequence;
```
  
​  
### * function 조회 및 삭제
```
show function status;
drop function nextval;
```
