# 06. [세션 2 필수] 3대 하네스(Harness) 100% Green 자율 개선 프롬프트
> **사용 시점**: 실습 2부 (14~28분)  
> **상황**: 터미널에서 `python3 harness/check_harness.py`를 실행하여 3대 하네스(AST 보안 린터 + 단위테스트 + SLA 응답 지연)의 빨간불(RED GATE) 리포트를 마주했을 때 사용합니다.

---

### 📋 복사용 프롬프트 (아래 내용을 그대로 AI 에이전트에 전달하세요)

```text
[역할] 너는 네이버 수준의 엔터프라이즈 수석 소프트웨어 아키텍트이자 보안 엔지니어다.
[미션] 우리 프로젝트에 하네스 검증 엔진(harness/check_harness.py)과 사내 표준 가이드라인(harness/AGENTS.md)이 준비되어 있다.

1. 먼저 터미널에서 `python3 harness/check_harness.py`를 직접 실행하고 결과를 확인해라.
2. harness/AGENTS.md 표준을 100% 준수하도록 main.py 코드를 스스로 리팩토링해라:
   - 하드코딩된 Secret/Token은 os.getenv() 및 안전한 기본값으로 격리
   - 모든 SQL 쿼리는 SQLite 파라미터화 바인딩(?) 표준으로 수정
   - O(N^2) 선형 탐색 로직은 set()을 이용한 O(1) 해시 룩업으로 최적화
   - 동시성 DB 락(database is locked) 병목 방어를 위해 SQLite WAL 모드(PRAGMA journal_mode=WAL) 및 busy_timeout 설정
3. tests/test_api.py 파일을 생성하고 pytest 기반의 단위 테스트 4개 이상을 작성해라:
   - 기본 CRUD 정상 동작 검증
   - SQL Injection 공격 구문 입력 시 DB가 보호되는지 검증
   - 잘못된 관리자 토큰 입력 시 401 또는 403 거부 검증
   - 빈 제목(empty title) 등 유효하지 않은 입력 방어 검증
4. 수정 후 터미널에서 `python3 harness/check_harness.py`를 다시 실행하여, 3개 스테이지가 모두 [100% GREEN 통과]할 때까지 스스로 오류를 분석하고 자율 수정 루프(Self-Healing Loop)를 반복해라.
```

---

### 🔍 하네스 최종 통과 확인 (터미널)
```bash
python3 harness/check_harness.py
```
* 기대 출력:
  * `[Stage 1] AST Security Scan: ✅ 0건 통과`
  * `[Stage 2] Unit Tests: ✅ PASS (4 passed)`
  * `[Stage 3] SLA Benchmark: ✅ PASS (p99 < 100ms)`
  * **`🎉 [ALL GREEN] 모든 엔터프라이즈 하네스 품질 게이트를 통과했습니다!`**
