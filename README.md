## DainWiki

- BookStack 간편하게 사용하기 위한 초기 설정 버전  
- **추후 팀프로젝트 구성원들과 간단하게 커뮤니케이션 문제 해결** 및 **DB 그룹 관련 데이터 통합**  
- Docker로 배포 및 백업  
- 개인 위키 운영  
  - https://dainwiki.com 
    ▸ 개인위키는 AWS LightSail $12 요금제 활용중  


## 사용법

- docker, docker compose 설치  
- docker-compose up  

```bash
docker-compose up -d
```

## 수동 백업

```bash
./scripts/backup.sh
```

## 자동 백업
- crontab에 scripts/backup_and_git_push.sh 실행하도록 설정
```
crontab -e
0 */3 * * * /path/to/bookstack/db-group-bookstack/scripts/backup_and_git_push.sh >> /path/to/bookstack/db-group-bookstack/auto_backup.log 2>&1
```

## 복구
```bash
./scripts/restore.sh ./backups/{{filename}}.sql
```


## ✍️ 향후 계획

- 사용자 인증 기능 설정
- 문서 템플릿 개선
- 팀원 초대 및 권한 관리
- 태그 및 문서 버전 관리 기능 확장
