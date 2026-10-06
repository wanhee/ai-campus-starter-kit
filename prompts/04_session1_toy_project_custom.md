# 04. [세션 1] 자유 주제 커스텀 REST API 구현 프롬프트
> **사용 시점**: 실습 1부 (05~15분)  
> **추천 대상**: 나만의 독창적인 아이디어(맛집 지도, 게임 전적, 음악 플레이리스트 등)로 구현하고 싶은 학생

---

### 📋 복사용 프롬프트 템플릿
* `[내 서비스 주제]`와 `[데이터 항목]` 부분만 본인의 아이디어로 바꾸어 AI에게 전달하세요:

```text
FastAPI(파이썬)를 사용하여 '[내 서비스 주제]' REST API 백엔드를 main.py 단일 파일로 만들어줘.
현재 main.py에 작성된 아키텍처 규칙과 기본 DB 구조, 함수 스타일을 유지하면서 아래 4가지 요구사항을 추가해줘:

1. [기본 CRUD]: 아이템 모델(id, title, description, tags, created_at)을 SQLite에 저장하고 전체 목록을 조회하는 API (GET /items, POST /items)
2. [키워드 검색]: GET /items/search?q={keyword} 엔드포인트에서 제목이나 설명에 키워드가 포함된 아이템을 DB에서 검색하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/items/{id}에서 관리자 토큰을 검증하여 항목을 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /items/filtered 엔드포인트에서 사전에 정의된 차단 태그 목록(blocked_tags = ["spam", "ad", "private", "temp"])에 해당하는 항목을 제외한 클린 목록을 반환해줘.

빠르게 로컬에서 uvicorn으로 띄울 수 있게 main.py 코드를 완성해줘.
```

---

### 🔍 동작 검증 명령어 (터미널)
```bash
uvicorn main:app --reload --port 8000
# http://localhost:8000/docs
```
