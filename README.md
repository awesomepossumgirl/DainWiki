## DainWiki

- 📌 **개인 위키 프로젝트** (시작일: 2025.01.05~)
  - http://dainwiki.com 
- BookStack 간편하게 사용하기 위한 초기 설정 버전
- 목적: 트러블슈팅, 개발 지식 문서화
- **추후 협업 시 지식 공유 기반 커뮤니케이션 문제 해결** 및 **DB 그룹 관련 데이터 통합**  
- Docker로 배포 및 백업  

## 기술스택

- **Frontend**: BookStack (Laravel 기반 Wiki 플랫폼) API
- **Backend**: MariaDB  
- **DevOps**: Docker, AWS
   - 개인위키는 AWS LightSail $12 요금제 활용중

  
## 주요 기능

- 책장 → 책 → 챕터 → 구조 (에러 해결, 라이브러리 사용법, 코드 분석 등) 정리
- 검색 가능한 위키 시스템
- 협업 대비 문서 구조 설계


## 프로젝트 구조
- 전체 디렉토리 구조(Docker 기반 BookStack + MariaDB 구성 기준)
- HTTPS 접속용
  - `cert/`, `html/`, `vhost.d/`는 SSL와 리버스 프록시용

```bash
📁 DainWiki/
├── 📁 bookstack/         # BookStack 컨테이너 설정 및 데이터
│   └── ...                # 도커 이미지에서 마운트됨
├── 📁 bookstack_db/      # MariaDB 데이터
│   └── ...                  # (.frm, .ibd 등 DB 파일들)
├── 📁 certs/             # 인증서 저장소 (자동 생성됨)
├── 📁 html/              # nginx 기본 페이지 저장소
├── 📁 vhost.d/           # 가상 호스트 설정 (자동 생성됨)
├── 📄 docker-compose.yml   # 전체 도커 설정
```


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
- 보안 인증 → https:// 연결
  
