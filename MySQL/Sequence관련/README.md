## Sequence 관련

### * Sequence 조회
```
$SELECT AUTO_INCREMENT AS nextval FROM information_schema.TABLES
WHERE TABLE_SCHEMA = DATABASE()
AND TABLE_NAME='테이블명';
```

  
### * Sequence 초기화 
```
$ALTER TABLE 테이블명 auto_increment=1;
```