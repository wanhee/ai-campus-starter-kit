# 02. [세션 1] 날씨 기반 옷차림 & 일정 추천 서비스 구현 프롬프트
> **사용 시점**: 실습 1부 (05~15분)  
> **추천 대상**: 라이프스타일/생활 밀착형 서비스를 선호하는 학생

---

### 📋 복사용 프롬프트 (아래 박스 내용을 그대로 AI에게 전달하세요)

```text
FastAPI(파이썬)를 사용하여 '날씨 기반 옷차림 & 행동 추천 서비스' 백엔드를 main.py 단일 파일로 만들어줘.
현재 main.py에 작성된 아키텍처 규칙과 기본 DB 구조, 함수 스타일을 유지하면서 아래 4가지 요구사항을 추가해줘:

1. [기본 CRUD]: 추천 아이템(id, city, temp, weather_desc, outfit_recommendation, tags)을 SQLite에 저장하고 전체 목록을 조회하는 API (GET /weather, POST /weather)
2. [키워드 검색]: GET /weather/search?q={keyword} 엔드포인트에서 도시 이름이나 추천 의상 키워드로 DB를 검색하여 반환해줘.
3. [관리자 인증]: POST /admin/login 엔드포인트에서 관리자 비밀번호를 확인하여 토큰을 발급하고, DELETE /admin/weather/{id}에서 관리자 토큰을 검증해 삭제하는 기능 구현.
4. [차단 태그 필터링]: GET /weather/filtered 엔드포인트에서 사전에 정의된 위험 기상 태그(blocked_tags = ["tornado", "typhoon", "blizzard", "hail"])가 포함된 항목을 제외한 안전한 날씨 추천 목록을 반환해줘.

빠르게 로컬에서 uvicorn으로 띄울 수 있게 main.py 코드를 완성해줘.
```

---

### 🔍 동작 검증 명령어 (터미널)
```bash
uvicorn main:app --reload --port 8000
# http://localhost:8000/docs
```
