# 💡 실습 세션 1: 15분 완성 토이 프로젝트 프롬프트 프리셋
> 학생 각자 관심 있는 주제 1개를 선택하여 ChatGPT, Claude, Cursor 등 선호하는 AI 도구에 붙여넣어 초기 토이 프로젝트를 15분 만에 생성합니다.  
> **모든 프롬프트는 `MINIMUM_FEATURE_SPEC.md`의 4대 필수 기능 요건(CRUD, 검색, 관리자 인증, 차단 태그 필터링)을 공통으로 만족하도록 최적화되어 있습니다.**

---

### [옵션 1] 개인 일정 & Todo 관리 REST API (추천: 백엔드/기초)
> **목표**: 할 일 추가, 조회, 키워드 검색, 관리자 인증, 차단 태그 필터링 기능을 가진 경량 웹 API

```text
FastAPI(파이썬)를 사용하여 할 일(Todo) 관리 REST API 백엔드를 main.py 단일 파일로 만들어줘.
요구사항:
1. [기본 CRUD]: SQLite 데이터베이스(todo.db)를 사용하여 데이터를 저장해줘. 모델은 id, title, description, is_completed, created_at, tags (콤마 구분 문자열) 필드를 가져야 해. (GET /todos, POST /todos)
2. [키워드 검색]: GET /todos/search?q={keyword} 엔드포인트에서 제목(title)이나 설명(description)에 키워드가 포함된 할 일을 DB에서 조회하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/todos/{id}에서 관리자 토큰을 검증하여 항목을 삭제하는 기능을 구현해줘.
4. [차단 태그 필터링]: GET /todos/filtered 엔드포인트에서 사전에 정의된 차단 태그 목록(blocked_tags = ["spam", "ad", "private", "temp"])에 해당하는 항목을 제외한 클린 할 일 목록을 반환해줘.
빠르게 로컬에서 uvicorn으로 띄울 수 있게 작성해줘.
```

---

### [옵션 2] 날씨 기반 옷차림 & 일정 추천 서비스 (추천: 풀스택)
> **목표**: 가상 날씨 데이터를 기반으로 추천 아이템 조회, 검색, 관리자 등록, 금지 지역 필터링 기능 제공

```text
FastAPI(파이썬)를 사용하여 '날씨 기반 옷차림 & 행동 추천 서비스' 백엔드를 main.py 단일 파일로 만들어줘.
요구사항:
1. [기본 CRUD]: 추천 아이템(id, city, temp, weather_desc, outfit_recommendation, tags)을 SQLite(weather.db)에 저장하고 전체 목록을 조회하는 API (GET /weather, POST /weather)
2. [키워드 검색]: GET /weather/search?q={keyword} 엔드포인트에서 도시 이름이나 추천 의상 키워드로 DB를 검색하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/weather/{id}에서 관리자 토큰을 검증해 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /weather/filtered 엔드포인트에서 사전에 정의된 위험 기상 태그(blocked_tags = ["tornado", "typhoon", "blizzard", "hail"])가 포함된 항목을 제외한 목록을 반환해줘.
빠르게 로컬에서 uvicorn으로 띄울 수 있게 작성해줘.
```

---

### [옵션 3] 개발자를 위한 기술 아티클 북마크 & 요약기 (추천: 데이터/검색)
> **목표**: 읽은 기술 블로그 링크를 저장하고, 키워드 검색, 관리자 권한, 스팸 태그 필터링 기능 제공

```text
FastAPI(파이썬)를 사용하여 '기술 아티클 북마크 저장소' 백엔드를 main.py 단일 파일로 만들어줘.
요구사항:
1. [기본 CRUD]: 아티클(id, url, title, summary, category, tags)을 SQLite(bookmark.db)에 저장하고 전체 목록을 조회하는 API (GET /bookmarks, POST /bookmarks)
2. [키워드 검색]: GET /bookmarks/search?q={keyword} 엔드포인트에서 제목(title)이나 요약(summary)에 키워드가 포함된 아티클을 DB에서 검색해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/bookmarks/{id}에서 관리자 토큰을 검증해 북마크를 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /bookmarks/filtered 엔드포인트에서 사전에 정의된 광고 태그(blocked_tags = ["ad", "clickbait", "gambling", "crypto_spam"])가 포함된 아티클을 제외한 목록을 반환해줘.
빠르게 로컬에서 uvicorn으로 띄울 수 있게 작성해줘.
```

---

### [옵션 4] 캠퍼스 미니 커뮤니티 익명 게시판 (추천: 커뮤니티)
> **목표**: 학과 익명 게시글 작성, 키워드 검색, 관리자 글 삭제, 유해 태그 필터링 기능 제공

```text
FastAPI(파이썬)를 사용하여 '대학교 익명 커뮤니티 게시판 API' 백엔드를 main.py 단일 파일로 만들어줘.
요구사항:
1. [기본 CRUD]: 게시글(id, author, title, content, likes, tags)을 SQLite(board.db)에 저장하고 목록을 조회하는 API (GET /posts, POST /posts)
2. [키워드 검색]: GET /posts/search?q={keyword} 엔드포인트에서 제목이나 내용에 키워드가 포함된 글을 DB에서 검색하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/posts/{id}에서 관리자 토큰을 검증해 글을 강제 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /posts/filtered 엔드포인트에서 사전에 정의된 욕설/비방 태그(blocked_tags = ["abuse", "hate", "leak", "spoiler"])가 포함된 글을 제외한 클린 피드를 반환해줘.
빠르게 로컬에서 uvicorn으로 띄울 수 있게 작성해줘.
```

---

### 💡 학생용 자유 주제 작성 공식 (Custom Topic)
만약 본인이 원하는 다른 주제(반려동물 다이어리, 음악 플레이리스트, 주식 메모 등)로 만들고 싶다면, 아래 템플릿에 주제명만 바꿔서 AI에게 요청하면 됩니다:

```text
FastAPI(파이썬)를 사용하여 [내 주제명] REST API 백엔드를 main.py 단일 파일로 만들어줘.
반드시 아래 4가지 기능을 모두 포함해야 해:
1. [기본 CRUD]: 모델(id, title, content, tags)을 SQLite(app.db)에 저장하고 전체 조회 (GET /items, POST /items)
2. [키워드 검색]: GET /items/search?q={keyword} 엔드포인트에서 제목이나 내용으로 DB 검색
3. [관리자 인증]: POST /admin/login에서 관리자 토큰 발급 및 DELETE /admin/items/{id}에서 관리자 토큰 검증 삭제
4. [차단 태그 필터링]: GET /items/filtered에서 차단 태그(blocked_tags) 목록에 해당하는 아이템을 제외한 클린 목록 반환
빠르게 uvicorn으로 띄울 수 있게 작성해줘.
```
