# 🚀 Campus AI Engineering Lab Starter Kit
> **특강 주제**: AI 시대의 개발과 개발자의 역할: 엔터프라이즈 환경과 하네스 엔지니어링  
> **강사**: 김완희 (네이버 13년차 개발자)  
> **목표**: 80분 집중 핸즈온을 통해 AI 초고속 구현 ➔ CI 보안 반려 ➔ 자율 치유 ➔ 3대 하네스 구축까지 실무 엔지니어링 사이클 완주

---

## ⚡ 빠른 시작 (3초 세팅)

1. 저장소 우측 상단의 초록색 **[Use this template]** ➔ **[Create a new repository]** 클릭
2. Repository name 입력 후 **반드시 `Public`** 선택! (Private 선택 시 Actions 실행 제한 가능)
3. 생성된 본인 저장소를 로컬 컴퓨터로 클론:
   ```bash
   git clone https://github.com/<본인_GITHUB_ID>/<저장소명>.git
   cd <저장소명>
   
   # 가상환경 생성 및 패키지 설치
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt pytest
   ```

---

## 🗺️ 실습 2개 세션 로드맵

### 🎬 [세션 1 (40분)] 토이 프로젝트 구현 & AI PR 리뷰어 격파
1. **기능 브랜치 생성**:
   ```bash
   git checkout -b feature/todo-service
   ```
2. **AI 에이전트로 기능 구현**:
   * 평소 사용하시는 AI 도구(Cursor, Claude Code, ChatGPT, Copilot 등)에 [`prompts/01_session1_toy_project_todo.md`](./prompts/01_session1_toy_project_todo.md)의 프롬프트를 복사하여 `main.py`에 필수 기능을 구현합니다. (날씨, 게시판 등 다른 주제는 [`prompts/`](./prompts/) 디렉토리 참고)
   * 로컬 서버 구동 테스트: `uvicorn main:app --reload --port 8000` (Swagger UI: `http://localhost:8000/docs`)
3. **커밋 & 푸시 후 GitHub에서 PR 생성**:
   ```bash
   git add main.py
   git commit -m "feat: implement Todo REST API with search, admin auth, and tag filtering"
   git push origin feature/todo-service
   ```
   * GitHub 웹에서 `main` 브랜치를 향해 **Pull Request(PR)**를 생성합니다.
4. **AI PR Reviewer의 자동 리뷰 확인**:
   * GitHub Actions 봇이 30초 내로 **CWE-89(SQLi), CWE-798(키 하드코딩), CWE-327(취약 해시), SLA 성능 병목** 4대 결함을 지적하며 반려(REQUEST_CHANGES)하는 것을 확인합니다.
5. **AI 자율 치유 (Self-Healing) & 머지**:
   * [`prompts/05_session1_pr_review_self_heal.md`](./prompts/05_session1_pr_review_self_heal.md) 프롬프트를 AI에게 전달하여 코드를 수정하게 한 뒤 다시 푸시합니다.
   * **100% Green (APPROVE)** 통과 확인 후 `main`에 머지합니다.

---

### 🎬 [세션 2 (40분)] 3대 하네스 구축 & 엔터프라이즈급 재구축
1. **3대 하네스 검증 엔진 실행**:
   ```bash
   python3 harness/check_harness.py
   ```
   * AST 정적 보안 린터(Stage 1), 단위 테스트(Stage 2), SLA 응답 지연 & DB 동시성 벤치마크(Stage 3) 검증 결과를 확인합니다.
2. **동시성 락 & 부하 시뮬레이션 (Before vs After 계측)**:
   ```bash
   python3 harness/simulate_load.py
   ```
   * 동시 쓰기 요청 시 SQLite 기본 락 병목(~34% 500 에러)과 WAL 모드 전환 후 무장애 완주(0.00% 에러율) 정량 지표를 측정합니다.
3. **사내 엔지니어링 표준 규칙(`harness/AGENTS.md`) 기반 자율 리팩토링**:
   * AI 에이전트에게 [`prompts/06_session2_harness_self_heal.md`](./prompts/06_session2_harness_self_heal.md) 프롬프트를 전달하여, 하네스가 100% 통과할 때까지 코드를 자율 수정하도록 지시합니다.
4. **상위 10% 포트폴리오 완성**:
   * 하네스 100% Green 통과 후, [`prompts/07_session2_portfolio_readme.md`](./prompts/07_session2_portfolio_readme.md) 프롬프트를 사용하여 본인 저장소의 `README.md`를 Before vs After 성능 개선 수치가 포함된 고품격 포트폴리오로 교체합니다.

---

## 📂 프로젝트 구조

```
├── .github/
│   └── workflows/
│       └── ai_pr_review.yml      # Zero-Key AI PR 자동 리뷰어 워크플로우
├── harness/
│   ├── check_harness.py          # 3대 하네스(보안 AST + 단위테스트 + SLA 지연) 검증 스크립트
│   ├── simulate_load.py          # 동시성 락(Lock) & 부하 시뮬레이션(Before vs After) 계측 스크립트
│   └── AGENTS.md                 # 사내 표준 엔지니어링 규칙 헌법
├── prompts/                      # 💡 단계별 복사용 실습 프롬프트 모음 (01~07)
│   ├── 01_session1_toy_project_todo.md
│   ├── 02_session1_toy_project_weather.md
│   ├── 03_session1_toy_project_board.md
│   ├── 04_session1_toy_project_custom.md
│   ├── 05_session1_pr_review_self_heal.md
│   ├── 06_session2_harness_self_heal.md
│   ├── 07_session2_portfolio_readme.md
│   └── README.md
├── templates/
│   └── README_PORTFOLIO_TEMPLATE.md # 세션 2 완성 포트폴리오 템플릿
├── main.py                       # 초기 시드 코드 (FastAPI + SQLite)
├── requirements.txt              # 기본 의존성 목록
└── README.md                     # 본 가이드 문서
```

---
*(본 스타터 킷은 학부생 대상 기술 워크숍을 위해 100% 사전 검증 및 최적화되었습니다.)*
