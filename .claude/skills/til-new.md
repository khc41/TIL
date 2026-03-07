---
name: til-new
description: 새로운 TIL 파일을 생성합니다. 카테고리를 입력받아 해당 폴더에 오늘 날짜로 md 파일을 생성하고 template.md 내용을 복사합니다.
---

# TIL 새 파일 생성

$ARGUMENTS를 카테고리로 받아서 다음 작업을 수행하세요:

1. 카테고리 매핑 확인:
   - mysql, jpa, sql, postgres, db → database-and-storage/relational-database/
   - nosql, elasticsearch, mongodb, redis-data → database-and-storage/nosql/
   - db-architecture, sharding, replication → database-and-storage/architecture/
   - kafka, mq, rabbitmq, sqs → distributed-systems/message-queue/
   - system-design, scalability, architecture → distributed-systems/system-design/
   - microservices, ddd, msa → distributed-systems/microservices/
   - redis, cache, caching → cache-and-performance/cache-strategy/
   - lock, concurrency, distributed-lock → cache-and-performance/concurrency/
   - performance, optimization, tuning → cache-and-performance/performance-tuning/
   - java, virtual-threads, thread → java-and-jvm/java-core/
   - gc, garbage-collection, memory → java-and-jvm/garbage-collection/
   - code-quality, refactoring, clean-code → code-quality/improvement-series/
   - best-practices, review → code-quality/best-practices/
   - spring, spring-boot, spring-framework → infrastructure-and-devops/spring-framework/
   - api, rest, sse, websocket → infrastructure-and-devops/realtime-api/
   - ai, llm, mcp, ai-tool → ai-and-automation/ai-tools/
   - conference, kakao, seminar → conferences/
   - book, ddia → books/designing-data-intensive-applications/
   - system-design-book → books/system-design-interview/

2. 오늘 날짜로 파일명 생성 (YYYY-MM-DD.md 형식)

3. template.md 파일을 읽어서 새 파일에 복사

4. 생성된 파일 경로를 사용자에게 알려주고 파일 열기 안내

**중요**: 만약 카테고리가 매핑되지 않으면 사용자에게 카테고리 목록을 보여주고 선택하도록 요청하세요.
