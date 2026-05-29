# claude-ppt-skill

**Claude Code 전용 PPT 기획·생성 스킬**
3라운드 인터랙션으로 목적→청중→디자인까지 먼저 설계한 뒤 발표자료를 만듭니다.

> "PPT를 바로 만들지 않는다. 먼저 기획하고, 그다음 생성한다."

---

## 특징

| 항목 | 내용 |
|------|------|
| 디자인 스타일 | **20가지** (P01 미니멀 SaaS → P20 어린이 교육) |
| 컬러 팔레트 | **8가지** (Royal Blue, Editorial Black, Marketing Navy 등) |
| 폰트 | **14가지** (Pretendard, Noto Sans KR, IBM Plex Sans KR 등) |
| 미리보기 | `references/design-menu.html` 브라우저로 열기 (미니 슬라이드 3장씩 미리보기) |
| 기획 인터랙션 | **3라운드** — 목적/청중/메시지 → 스토리라인/서식 → 컬러/폰트/스타일 |

---

## 설치

```bash
# 방법 1 — Claude Code 프로젝트 스킬로 등록
mkdir -p .claude/skills/ppt-maker
cp SKILL.md .claude/skills/ppt-maker/
cp -r references .claude/skills/ppt-maker/

# 방법 2 — 글로벌 스킬로 등록
mkdir -p ~/.claude/skills/ppt-maker
cp SKILL.md ~/.claude/skills/ppt-maker/
cp -r references ~/.claude/skills/ppt-maker/
```

---

## 사용법

Claude Code에서 PPT 관련 요청을 하면 자동으로 이 스킬이 실행됩니다.

**트리거 예시:**
```
PPT 만들어줘
발표자료 만들어줘
슬라이드 만들어
pptx 만들어
제안서 만들어
강의자료 만들어
보고서 PPT 만들어
```

---

## 3라운드 기획 흐름

```
라운드 1 — 목적 · 청중 · 핵심 메시지
  Q1. 이 PPT는 왜 만드나요?  (발표용 / 제출용 / 제안서 / 교육 / 보고 / 소개서)
  Q2. 주요 청중은 누구인가요?  (임원 / 투자자 / 고객 / 학습자 / 내부팀 / 심사위원)
  Q3. 청중이 기억할 핵심 메시지를 한 문장으로

라운드 2 — 스토리라인 · 레퍼런스 · 서식
  Q4. 설득 순서  (문제→해결 / 개념→실습 / Before→After / 시장→성장 등)
  Q5. 디자인 레퍼런스  (선택 사항)
  Q6. 비율 / 밀도 / 장수

라운드 3 — 컬러 · 폰트 · 스타일
  Step 7. 컬러 팔레트 선택 (8가지)
  Step 8. 폰트 선택 (14가지)
  Step 9. 디자인 스타일 선택 (20가지)
```

모든 선택이 끝나면 기획안 확정 → 슬라이드 아웃라인 → 슬라이드 본문 생성 → QA 체크 순서로 진행됩니다.

---

## 디자인 스타일 20가지 (P01–P20)

| 번호 | 스타일명 | 추천 용도 |
|------|----------|----------|
| P01 | 미니멀 B2B SaaS | 서비스 소개·SaaS |
| P02 | 따뜻한 교육자료 | 튜토리얼·교육 |
| P03 | 절제된 금융/전략 보고서 | 전략 보고·컨설팅 |
| P04 | 스타트업 IR | IR·피칭 |
| P05 | 감성 브랜드 소개서 | 브랜드·소개서 |
| P06 | AI/IT 강의자료 | AI·IT 강의 |
| P07 | 모던 다크 컨트라스트 | 개발자·테크 |
| P08 | 에디토리얼 매거진 | 인사이트·트렌드 |
| P09 | 웰니스/시니어 친화 | 헬스케어·복지 |
| P10 | 카드뉴스 스타일 발표 | 콘텐츠·요약 |
| P11 | 핀테크 클린 | 금융·결제 |
| P12 | 일본 와비사비 미니멀 | 문화·고급 브랜드 |
| P13 | 모바일 앱 출시 | 앱 런칭·제품 |
| P14 | 럭셔리 블랙 | 고급 브랜드·제안 |
| P15 | 이커머스 활기 | 쇼핑·프로모션 |
| P16 | 비영리/공익 | 공익·임팩트 보고 |
| P17 | 건축/부동산 | 건축·부동산 |
| P18 | 데이터 시각화 중심 | KPI·대시보드·분석 |
| P19 | 한국 트렌디 (당근·배민) | 한국 서비스·앱 |
| P20 | 어린이/교육 동심 | 어린이 교육·학습 |

각 스타일의 실제 슬라이드 분위기는 `references/design-menu.html`을 브라우저로 열어 미니 슬라이드 미리보기로 확인하세요.

---

## 파일 구조

```
claude-ppt-skill/
├── SKILL.md                      ← Claude Code 스킬 본체
├── LICENSE                       ← MIT
└── references/
    ├── design-menu.html          ← 디자인 메뉴 (브라우저로 열기)
    │                                컬러 8가지 + 폰트 14가지 + 스타일 20가지
    │                                미니 슬라이드 3장씩 미리보기 포함
    └── prompt.md                 ← 복사용 프롬프트 (PPT 생성 + 레퍼런스 적용)
```

---

## 생성 원칙 (자동 적용 금기사항)

- 과한 그라데이션 금지
- 의미 없는 아이콘 남발 금지
- 제목 아래 의미 없는 가로선 금지
- 본문 임의 왜곡 금지
- 텍스트 넘침 금지

---

## 폰트 다운로드

| 폰트 | 다운로드 |
|------|---------|
| Pretendard | https://github.com/orioncactus/pretendard |
| Noto Sans KR | https://fonts.google.com/noto/specimen/Noto+Sans+KR |
| Noto Serif KR | https://fonts.google.com/noto/specimen/Noto+Serif+KR |
| IBM Plex Sans KR | https://fonts.google.com/specimen/IBM+Plex+Sans+KR |
| Nanum Gothic | https://fonts.google.com/specimen/Nanum+Gothic |
| Nanum Myeongjo | https://fonts.google.com/specimen/Nanum+Myeongjo |
| Gowun Dodum | https://fonts.google.com/specimen/Gowun+Dodum |
| Hahmlet | https://fonts.google.com/specimen/Hahmlet |
| Black Han Sans | https://fonts.google.com/specimen/Black+Han+Sans |
| Do Hyeon | https://fonts.google.com/specimen/Do+Hyeon |
| Montserrat | https://fonts.google.com/specimen/Montserrat |
| Poppins | https://fonts.google.com/specimen/Poppins |
| Work Sans | https://fonts.google.com/specimen/Work+Sans |
| Manrope | https://fonts.google.com/specimen/Manrope |

---

## 라이선스

MIT License — 자유롭게 사용, 수정, 배포 가능합니다.

---

© 2026 COMMME · Built with Claude Code
