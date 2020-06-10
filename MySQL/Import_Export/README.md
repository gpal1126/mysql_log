## Import와 Export

### * 덤프 방법
- 커맨드 창에서 mysqldump.exe 파일이 있는 경로로 이동
```
> cd C:\...생략\MySQL\MySQL Server 5.7\bin
```


### * Export
#### DB Export
- mysqldump -u 계정명 -p 데이터베이스명 > 저장될 파일명  
```
mysql > mysqldump -u root -p dbName > C:/sql/backup/dbName_20190630.sql 
```
#### 특정 테이블 Export
- mysqldump -u 계정명 -p 데이터베이스명 백업할테이블명 > 저장될 파일명  
```
mysql > mysqldump -u root -p dbName tableName > C:/sql/backup/dbName_tableName_20190630.sql 
```

#### 다른 서버의 DB Export
- mysqldump -u 계정명 -p 데이터베이스명 --port=포트번호 -h IP주소 > 저장될 파일명  
```
mysql > mysqldump -u root -p dbName --port=3306 -h 127.0.0.1 > C:/sql/backup/dbName_20190630.sql 
```
#### 다른 서버의 특정 테이블 Export  
- mysqldump -u 계정명 -p 데이터베이스명 --port=포트번호 -h IP주소 백업할테이블명 > 저장될 파일명  
```
mysql > mysqldump -u root -p dbName --port=3306 -h 127.0.0.1 tableName > C:/sql/backup/dbName_tableName_20190630.sql 
```
​

​

### * Import
#### DB Import
- mysql -u 계정명 -p 데이터베이스명 < 임포트할파일명  
```
mysql > mysql -u root -p dbName < C:/sql/backup/dbName_20190630.sql 
```

#### 다른 서버의 DB Import  
- mysql -u 계정명 -p 데이터베이스명 --port=포트번호 -h IP주소 < 임포트할파일명  
```
mysql > mysql -u root -p dbName --port=3306 -h 127.0.0.1 < C:/sql/backup/dbName_20190630.sql 
```