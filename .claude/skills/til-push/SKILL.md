---
name: til-push
description: 작성한 TIL 문서를 README에 자동으로 추가하고 Git commit & push 합니다. 변경된 파일을 자동으로 감지합니다.
---

# TIL Push

인자 없이 실행됩니다. 변경된 TIL 파일을 자동으로 감지하여 처리합니다:

1. 변경된 TIL 파일 자동 감지
   - `git diff origin/master --name-only`로 현재 브랜치와 원격 master 비교
   - 만약 로컬 커밋이 없다면 `git status --short`로 untracked/modified 파일 감지
   - `.md` 확장자이고 카테고리 폴더 내에 있는 파일만 대상 (README.md, template*.md 제외)
   - 감지된 파일이 없으면 사용자에게 알림 후 종료
   - 감지된 파일이 여러 개이면 사용자에게 목록을 보여주고 어떤 파일인지 확인

2. 파일을 읽어서 제목 추출
   - 파일 내 첫 번째 `#` 또는 `##` 헤딩에서 이모지를 제거한 텍스트를 제목으로 사용
   - 예: `# 📅 2026-03-07` → 날짜만 있으면 그 다음 헤딩 사용
   - 예: `## 레디스 캐시 전략` → "레디스 캐시 전략"

3. 파일 경로로 카테고리 파악
   - database-and-storage/relational-database/ → Relational Database
   - database-and-storage/nosql/ → NoSQL
   - database-and-storage/architecture/ → Database Architecture
   - distributed-systems/message-queue/ → Message Queue
   - distributed-systems/system-design/ → System Design
   - distributed-systems/microservices/ → Microservices
   - cache-and-performance/cache-strategy/ → Cache Strategy
   - cache-and-performance/concurrency/ → Concurrency
   - cache-and-performance/performance-tuning/ → Performance Tuning
   - java-and-jvm/java-core/ → Java Core
   - java-and-jvm/garbage-collection/ → Garbage Collection
   - code-quality/improvement-series/ → Code Quality Improvement
   - code-quality/best-practices/ → Best Practices
   - infrastructure-and-devops/spring-framework/ → Spring Framework
   - infrastructure-and-devops/realtime-api/ → Realtime API
   - ai-and-automation/ai-tools/ → AI Tools
   - ai-and-automation/if-kakao-2025/ → if kakao 2025
   - conferences/ → Conferences
   - books/designing-data-intensive-applications/ → DDIA Book
   - books/system-design-interview/ → System Design Book

4. 상위 카테고리 INDEX.md 업데이트
   - INDEX.md는 **상위 카테고리 폴더** 하나에만 존재 (하위 폴더에 별도 생성 금지)
     - `database-and-storage/INDEX.md`, `distributed-systems/INDEX.md` 등
     - `database-and-storage/nosql/INDEX.md` 같은 하위 폴더 INDEX.md는 만들지 않음
   - INDEX.md 내부는 하위 디렉토리별로 `## subdirectory-name` 섹션 헤더로 구분
   - 형식: `- [YYYY-MM-DD - 제목](./하위폴더/파일명.md)`
   - 같은 섹션 내에서 날짜 역순으로 정렬 (최신이 위로)
   - README.md는 건드리지 않음 (수동 관리)
   - INDEX.md가 없으면 새로 생성, 있으면 해당 섹션에 항목 추가

5. Git 작업 (로컬 커밋 + 원격 푸시):
   ```bash
   git add <til-file> <상위-category>/INDEX.md
   git commit -m "Add TIL: [추출된 제목]

   Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>"
   git push origin master
   ```

6. 성공 메시지 출력
   - 커밋 완료
   - 원격 저장소(origin master)에 푸시 완료
   - 파일 경로 및 제목 표시

**Note**:
- 파일 경로를 직접 입력할 필요 없이 자동으로 감지합니다.
- INDEX.md는 최상위 카테고리 폴더에만 하나씩 존재하며, 하위 폴더별로 섹션을 나눠 관리합니다.
- README.md는 수동 관리 (각 카테고리 INDEX.md로의 링크만 포함).
- 로컬 커밋 후 자동으로 원격 저장소에 푸시됩니다.
