# 07. [세션 2 피날레] 상위 10% 포트폴리오 README 작성 프롬프트
> **사용 시점**: 실습 2부 (35~40분)  
> **목표**: 단순한 "AI로 Todo 만들었습니다" 수준의 학부생 과제를, 대기업/빅테크 기술 면접관을 사로잡는 **"보안 가드레일과 3대 하네스로 검증된 엔터프라이즈 포트폴리오"**로 승격시킵니다.

---

### 📋 복사용 프롬프트 (아래 내용을 그대로 AI에게 전달하세요)

```text
우리가 지금까지 완성한 프로젝트의 README.md를 기술 채용 시장에서 상위 10% 평가를 받을 수 있는 '엔터프라이즈 엔지니어링 포트폴리오' 형태로 전면 재작성해줘.

`templates/README_PORTFOLIO_TEMPLATE.md`의 구조를 완벽히 반영하여 다음 섹션을 반드시 포함해줘:
1. [프로젝트 헤더]: 서비스 이름과 함께 'CI/CD 하네스 통과', '보안 취약점 0건', 'SLA 100ms 충족' 뱃지 표기
2. [아키텍처 다이어그램]: Mermaid flowchart로 [Client -> FastAPI -> SQLite -> 3대 하네스 방어선] 도식화
3. [Before vs After 정량적 성능 지연 개선표]:
   - O(N^2) 중첩 루프 vs O(1) Hash Set 룩업
   - SQLite 동시성 파일 락(~34% 500 에러) vs WAL 모드 전환(0.00% 무장애 완주)
   - 1,000건 동시 요청 시 응답 지연 시간(Latency) 및 처리량(RPS) 단축 수치
4. [보안 가드레일 (CWE Top 25 방어 내역)]:
   - CWE-89 (SQL Injection) -> SQLite 파라미터 바인딩
   - CWE-798 (하드코딩 자격증명) -> os.getenv 환경변수 격리
   - CWE-327 (취약 해시) -> SHA-256 + Salt
5. [3대 하네스(Campus Harness) 검증 결과]:
   - check_harness.py Stage 1(AST 린터), Stage 2(단위 테스트), Stage 3(SLA 벤치마크) All Green 통과 로그 요약
6. [설치 및 실행 방법]: 30초 퀵스타트 가이드

단순 기능 나열이 아니라, "AI가 만든 코드의 결함을 엔지니어링 하네스로 어떻게 방어하고 검증했는가"가 돋보이도록 마크다운으로 깔끔하게 작성해줘.
```

---

### 🚀 포트폴리오 박제 및 완료
AI가 작성한 내용을 본인 저장소의 `README.md`에 저장하고 커밋 & 푸시합니다:

```bash
git add README.md
git commit -m "docs: finalize enterprise portfolio README with harness verification metrics"
git push origin <본인브랜치명>
```

👉 본인 GitHub 저장소 메인 화면을 새로고침하면 멋진 엔터프라이즈 포트폴리오가 완성됩니다!
