## 데이터베이스 생성 / 계정 생성 및 권한 추가

## 데이터베이스 생성 및 인코딩 설정   
- create database '데이터베이스명' DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;  
```
mysql > create database dbName DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```

### 데이터베이스 조회  
```
mysql > show databases;
```

### DB 계정 정보 조회  
- Mysql 5.7 이상 버전은 password -> authentication_string 로 변경됨  

```
mysql> use mysql;
mysql> select Host, User, Password from user;
# Mysql 5.7 이상 버전
mysql> select Host, User, authentication_string from user;
```  
​
### 보안을 위해 root 계정 말고 다른 이름으로 변경하자. 
```
mysql> update user set user='new_user' where user='root';
```


### root 계정의 이름을 변경해서 사용하자.(특정 ip만 접근하도록 하면 더욱 좋다.)  
### 데이터베이스마다 서브 계정을 새로 하는 것도 좋다.(다만, 잘 적어놓자.)  
### 권한 부여 확인하기  

​

## 사용자 생성  
- grant all privileges on '데이터베이스명'.* to '계정명'@'%' identified by '비밀번호';  
    - '데이터베이스명'.* : 데이터베이스의 모든 테이블  
       @'%' : 모든 클라이언트 접근 가능  
```
mysql > grant all privileges on 'dbName'.* to 'userName'@'%' identified by 'password';
```

- grant all privileges on '데이터베이스명'.* to '계정명'@'IP' identified by '비밀번호';  
    -  '데이터베이스명'.* : 데이터베이스의 모든 테이블  
        @'IP' : 특정 IP 에서 접근 가능  
```
mysql > grant all privileges on 'dbName'.* to 'userName'@'127.0.0.1' identified by 'password';
```

## DBMS에 적용
- flush privileges;  
```
mysql > flush privileges;
```