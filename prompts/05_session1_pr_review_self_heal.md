# 05. [세션 1 필수] AI PR 리뷰 피드백 자율 치유 (Self-Healing) 프롬프트
> **사용 시점**: 실습 1부 (23~33분)  
> **상황**: PR을 생성하자마자 GitHub Actions `AI PR Code Reviewer` 봇이 4대 결함(CWE)을 지적하며 반려(`REQUEST_CHANGES` 또는 경고)했을 때 사용합니다.

---

### 📋 복사용 프롬프트 (아래 내용을 그대로 AI에게 전달하세요)

```text
GitHub Actions의 AI PR 리뷰 봇에서 우리 코드에 대해 다음 4가지 보안 취약점 및 성능 결함을 지적했습니다:

1. [CWE-89 SQL Injection]:
   - 원인: f-string을 이용한 동적 SQL 쿼리 작성으로 악의적 입력값 주입 위험.
   - 조치: SQLite 파라미터화 바인딩(?) 표준 방식으로 전면 교체해줘.

2. [CWE-798 Hardcoded Credentials]:
   - 원인: 관리자 토큰 및 Secret Key가 코드 내에 하드코딩되어 유출 위험.
   - 조치: `os.getenv("ADMIN_TOKEN", "fallback_dev_token")` 형태로 환경변수 분리 적용해줘.

3. [CWE-327 Broken Cryptography]:
   - 원인: 취약한 구식 MD5 단방향 해시 사용으로 충돌/레인보우 테이블 공격 위험.
   - 조치: `hashlib.sha256`에 Salt 문자열을 결합한 안전한 해싱 로직으로 교체해줘.

4. [SLA Performance Bottleneck]:
   - 원인: 차단 태그 필터링 시 중첩 반복문으로 O(N^2) 선형 탐색 병목 발생.
   - 조치: 루프 밖에서 `blocked_set = set(blocked_tags)`로 1회 생성 후 O(1) 해시 룩업으로 최적화해줘.

위 4가지 사항을 모두 반영하여 main.py를 안전하고 견고한 엔터프라이즈 코드로 리팩토링해줘.
기존 API 엔드포인트(CRUD, 검색, 인증, 차단 필터링)의 기능 동작은 100% 동일하게 유지되어야 해.
```

---

### 🚀 수정 후 학생 행동 지침
AI가 코드를 수정한 뒤, 터미널에서 변경 사항을 커밋하고 푸시합니다:

```bash
git add main.py
git commit -m "fix: resolve security vulnerabilities (CWE-89, 798, 327) and optimize SLA loop"
git push origin <본인브랜치명>
```

👉 푸시 후 GitHub PR 화면을 새로고침하면, 잠시 후 Actions 봇이 **✅ "모든 검사를 통과했습니다 (Green)"** 코멘트를 남깁니다!
