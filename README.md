# 🌐 DainWiki

+ 개인 위키 프로젝트 🐣
+ 코딩테스트 연습& 실전 코드 분석
+ 실제 업무중 트러블슈팅 기록용
+ 프로그래밍 언어, 서버, 네트워크 기술 자료 등 챕터 별로 정리
  + 주소 http://dainwiki.com
  + 추후 Docker로 마이그레이션 후 
  + AWS LightSail $3.5 요금제를 통해 배포할 예정
  + 또한 팀 프로젝트시 커뮤니케이션 문제 해결하기 위함 및 DB 그룹 관련 데이터 통합
 
    

# 🧰 현재 환경
- OS: Windows 10 / 11
- 로컬 웹서버: XAMPP (Apache + MySQL)
- 위키 엔진: [BookStack](https://www.bookstackapp.com/)  
- DB: MySQL

  
  
# 사용법🐳
+ docker, docker compose 설치
+ docker-compose up
<pre><code>docker-compose up -d</code></pre>
## 수동 백업
<pre><code>./scripts/backup.sh</code></pre>
## 자동 백업
+ crontab에 scripts/backup_and_git_push.sh 실행하도록 설정
<pre><code>crontab -e
0 */3 * * * /path/to/bookstack/db-group-bookstack/scripts/backup_and_git_push.sh >> /path/to/bookstack/db-group-bookstack/auto_backup.log 2>&1</code></pre>
## 복구
<pre><code>./scripts/restore.sh ./backups/{{filename}}.sql</code></pre>


# 인프라

