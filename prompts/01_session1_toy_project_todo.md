# 01. [세션 1] 할 일(Todo) 관리 REST API 구현 프롬프트
> **사용 시점**: 실습 1부 (05~15분)  
> **추천 대상**: 백엔드 표준 흐름을 가장 직관적으로 배우고 싶은 학생 (기본 추천!)

---

### 📋 복사용 프롬프트 (아래 박스 내용을 그대로 AI에게 전달하세요)

```text
FastAPI(파이썬)를 사용하여 할 일(Todo) 관리 REST API 백엔드를 main.py 단일 파일로 만들어줘.
현재 main.py에 작성된 아키텍처 규칙과 기본 DB 구조, 함수 스타일을 유지하면서 아래 4가지 요구사항을 추가해줘:

1. [기본 CRUD]: SQLite 데이터베이스를 사용하여 데이터를 저장해줘. 모델은 id, title, description, is_completed, created_at, tags (콤마 구분 문자열) 필드를 가져야 해. (GET /todos, POST /todos)
2. [키워드 검색]: GET /todos/search?q={keyword} 엔드포인트에서 제목(title)이나 설명(description)에 키워드가 포함된 할 일을 DB에서 조회하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/todos/{id}에서 관리자 토큰을 검증하여 항목을 삭제하는 기능을 구현해줘.
4. [차단 태그 필터링]: GET /todos/filtered 엔드포인트에서 사전에 정의된 차단 태그 목록(blocked_tags = ["spam", "ad", "private", "temp"])에 해당하는 항목을 제외한 클린 할 일 목록을 반환해줘.

빠르게 로컬에서 uvicorn으로 띄울 수 있게 main.py 코드를 완성해줘.
```

---

### 🔍 동작 검증 명령어 (터미널)
```bash
# 1. 서버 실행
uvicorn main:app --reload --port 8000

# 2. 브라우저에서 Swagger UI 접속 확인
# http://localhost:8000/docs
```
