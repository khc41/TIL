---
name: til-push
description: 작성한 TIL 문서를 README에 자동으로 추가하고 Git commit & push 합니다. 파일 경로를 인자로 받습니다.
---

# TIL Push

$ARGUMENTS로 받은 파일을 처리합니다:

1. 파일을 읽어서 제목 추출 (첫 번째 ## 제목)

2. 파일 경로로 카테고리 파악
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

3. 카테고리별 README 생성 또는 업데이트
   - 각 카테고리 폴더에 README.md 생성
   - 형식: `- [YYYY-MM-DD - 제목](./YYYY-MM-DD.md)`
   - 날짜 역순으로 정렬 (최신이 위로)

4. Git 작업:
   ```bash
   git add $ARGUMENTS <category>/README.md
   git commit -m "Add TIL: [제목]"
   git push origin master
   ```

5. 성공 메시지 출력

**Note**: 각 카테고리별 README.md를 자동으로 생성하여 파일 목록을 관리합니다.
