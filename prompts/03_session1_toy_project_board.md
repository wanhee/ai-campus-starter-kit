# 03. [세션 1] 캠퍼스 익명 커뮤니티 게시판 API 구현 프롬프트
> **사용 시점**: 실습 1부 (05~15분)  
> **추천 대상**: 에브리타임 등 커뮤니티 서비스 백엔드에 관심이 많은 학생

---

### 📋 복사용 프롬프트 (아래 박스 내용을 그대로 AI에게 전달하세요)

```text
FastAPI(파이썬)를 사용하여 '대학교 익명 커뮤니티 게시판 API' 백엔드를 main.py 단일 파일로 만들어줘.
현재 main.py에 작성된 아키텍처 규칙과 기본 DB 구조, 함수 스타일을 유지하면서 아래 4가지 요구사항을 추가해줘:

1. [기본 CRUD]: 게시글(id, author, title, content, likes, tags, created_at)을 SQLite에 저장하고 목록을 조회하는 API (GET /posts, POST /posts)
2. [키워드 검색]: GET /posts/search?q={keyword} 엔드포인트에서 제목이나 내용에 키워드가 포함된 글을 DB에서 검색하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/posts/{id}에서 관리자 토큰을 검증해 글을 강제 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /posts/filtered 엔드포인트에서 사전에 정의된 욕설/비방 태그(blocked_tags = ["abuse", "hate", "leak", "spoiler"])가 포함된 글을 제외한 클린 피드를 반환해줘.

빠르게 로컬에서 uvicorn으로 띄울 수 있게 main.py 코드를 완성해줘.
```

---

### 🔍 동작 검증 명령어 (터미널)
```bash
uvicorn main:app --reload --port 8000
# http://localhost:8000/docs
```
