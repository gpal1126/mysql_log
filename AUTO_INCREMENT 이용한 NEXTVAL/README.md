## AUTO_INCREMENT 이용한 NEXTVAL

MySQL에는 nextval이 따로 없다.
하지만, AUTO_INCREAMENT를 이용해서 간단하게 nextval을 가져올 수 있다.

​SELECT AUTO_INCREMENT AS nextval FROM information_schema.TABLES
WHERE TABLE_SCHEMA = DATABASE()
AND TABLE_NAME="테이블명";

```
mysql > SELECT AUTO_INCREMENT AS nextval 
FROM information_schema.TABLES 
WHERE TABLE_SCHEMA = DATABASE() 
AND TABLE_NAME="USER_TB";
```