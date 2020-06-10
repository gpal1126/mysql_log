## Function을 이용한 시퀀스  생성
   
   
### * 시퀀스 테이블 생성
```
CREATE TABLE SEQ(
    id INT NOT NULL, 
    seq_name VARCHAR(50) NOT NULL 
);
```
  
​  
### * 생성된 function 삭제
```
DROP FUNCTION IF EXISTS nextval;
```
  
  
### * Auto_increment 적용
```
DELIMITER $$ 
CREATE FUNCTION nextval (p_seq_name VARCHAR(45))
    RETURNS INT READS SQL DATA
BEGIN
    DECLARE RESULT_ID INT;
    UPDATE SEQ SET id = LAST_INSERT_ID(id+1) 
    WHERE seq_name = p_seq_name;
    SET RESULT_ID = (SELECT LAST_INSERT_ID());
    RETURN RESULT_ID;
END $$
DELIMITER ;
```
  
​  
### * 시퀀스 생성
```
INSERT INTO SEQ VALUES (0, 'test_seq');
```
  
​  
### * 시퀀스 조회
```
select nextval('test_seq');
```
  
​  
### * function 상태 조회 및 삭제
```
-- 현재 function 상태 조회
show function status;
-- function 삭제
drop function nextval;
```