## 쉘스크립트를 이용한 DB 자동 백업 설정 방법


### 1. 백업 받을 폴더 생성하기
```
$ mkdir /home/프로젝트명/backup
```

### 2. 백업 폴더의 권한 수정 소유자만 모두(읽기/쓰기/실행) 가능, 그 외 읽기/실행 가능
```
$ chmod 755 /home/프로젝트명/backup
```

### 3-1. backup.sh 배치 파일을 생성 및 편집
```
$ vi /home/프로젝트명/backup.sh
```

### 3-2. bakup.sh 파일에 백업 관련 내용 입력하기
```
# !/bin/sh
DATE=`date +"%Y%m%d%H%M"`
# 10일 전 날짜
# PREV_DATE=`date--date '10 days ago' +"%Y%m%d%H%M"`

/usr/bin/mysqldump -u유저ID -p패스워드 백업DB명 > /home/프로젝트명/backup/db_bak_${DATE}.sql
chown root.root /home/프로젝트명/backup/db_bak_${DATE}.sql
chmod 755 /home/프로젝트명/backup/db_bak_${DATE}.sql
# 10일 이전 백업 파일 삭제
# rm -Rf /home/프로젝트명/backup/db_bak_${PREV_DATE}.sql
```

### 4. backup.sh 파일 권한 주기 ( 파일 소유자만 실행 가능 )
```
$ chmod 100 /home/프로젝트명/backup.sh
```

### 5-1. crontab 설정 : 특정 시간에 자동 실행 
```
$ crontab -e
```

### 5-2. crontab 내용 수정
```
#vi 편집
00 02 * * * /home/프로젝트명/backup.sh
```

### 6. crond 서비스 재시작
```
$ service crond restart

Stopping crond:                                            [  OK  ]
Starting crond:                                            [  OK  ]
```

### 7. crontab 내용 확인
```
$ crontab -l

00 02 * * * /home/프로젝트명/backup.sh
```
