---
name: design-md
description: Stitch 공식 포맷(9섹션)에 맞춰 DESIGN.md 를 자동 생성. 브랜드 참조 URL · 기존 스크린샷 · 키워드로부터 디자인 시스템을 추출해 "소스 오브 트루스" 문서화.
source: google-labs-code/stitch-skills
language: ko
---

# 01. design-md — DESIGN.md 자동 생성

## 언제 사용하나

- 새 프로젝트를 시작할 때 **디자인의 뼈대를 먼저 문서화**하고 싶을 때
- 기존 스크린샷·Stitch 출력·브랜드 URL로부터 **재사용 가능한 스타일 토큰**을 뽑고 싶을 때
- 여러 화면·페이지를 **일관성 있게** 만들기 위한 기준서가 필요할 때

## 9섹션 표준 포맷

생성된 `DESIGN.md`는 반드시 아래 9섹션을 **모두 포함**해야 합니다.

```markdown
# [프로젝트 이름] 디자인 시스템

## 1. Visual Theme & Atmosphere (비주얼 테마 · 분위기)
- 전반적 무드: "따뜻한 파스텔 교실 감성", "미래적인 사이버 네이비" 등 자연어 서술
- 핵심 키워드 3–5개
- 디자인 철학 한 줄

## 2. Color Palette & Roles (색 팔레트 · 역할)
- 각 색은 **시적 이름 + HEX + 역할** 형태로 서술
- 예: "한강 새벽 블루 #3E5C76 — Primary · 주요 CTA"
- Primary · Secondary · Accent · Background · Surface · Text (Primary/Secondary) · Success · Warning · Danger 최소 9종

## 3. Typography Rules (타이포그래피)
- 기본 폰트: Pretendard Variable (한국어)
- 스케일: Display 48 / H1 36 / H2 28 / H3 22 / Body 17 / Small 14 / Caption 12
- 굵기 규칙: Heading 700, Body 400, Emphasis 600
- 줄간격(line-height): 본문 1.65, 제목 1.3

## 4. Component Stylings (컴포넌트)
- Button (Primary / Secondary / Ghost / Destructive) — Padding · Radius · Hover · Focus · Disabled 상태 모두
- Card — 그림자 · 테두리 · 라운드 · 내부 스페이싱
- Input — Placeholder · Focus Ring · Error 상태
- Badge · Tag · Chip

## 5. Layout Principles (레이아웃)
- 8pt 그리드 기본 (여백 단위: 4/8/12/16/24/32/48/64/96)
- 최대 콘텐츠 폭: 1200px
- 섹션 간 간격: 120px
- 그리드: 12컬럼 (데스크톱) / 4컬럼 (모바일)

## 6. Depth & Elevation (깊이 · 그림자)
- Level 0: 플랫 (그림자 없음)
- Level 1: `0 1px 3px rgba(0,0,0,0.06)` — 카드 기본
- Level 2: `0 10px 30px rgba(0,0,0,0.08)` — 호버 · 모달
- Level 3: `0 25px 50px rgba(0,0,0,0.15)` — 드롭다운 · 툴팁

## 7. Do's and Don'ts (해야 할 것 · 하지 말 것)
✅ Do
- 모든 한국어 요소에 `word-break: keep-all`
- Primary 버튼은 페이지당 1개만

❌ Don't
- 빨강+초록 조합으로 상태 표시 (색맹 고려)
- 본문을 14px 미만으로

## 8. Responsive Behavior (반응형)
- Breakpoints: sm 640 / md 768 / lg 1024 / xl 1280
- 모바일 우선: 기본 1컬럼, 768+ 에서 2–3컬럼
- 터치 타깃 최소 44×44px

## 9. Agent Prompt Guide (AI 프롬프트 가이드)
- 새 화면 요청 시 참조할 한 줄 요약 프롬프트
- 예: "따뜻한 파스텔 교실 테마로, Pretendard · 라운드 16px · 부드러운 그림자 중심으로 만들어 주세요."
```

## 사용 예시

### 예시 1. 브랜드 URL에서 추출
```text
사용자: @skills/01-design-md 로 toss.im 스타일의 DESIGN.md 를 만들어줘
AI: [스크린샷 분석 → 색 추출 → 9섹션 문서 생성 → DESIGN.md 파일로 저장]
```

### 예시 2. 키워드에서 생성
```text
사용자: "초등 3–4학년 · 환경 · 따뜻한 파스텔" 컨셉으로 DESIGN.md 작성
AI: [요구사항을 9섹션에 분배 → 팔레트 자동 생성 → 교육용 제약 반영]
```

## 품질 체크리스트

작성 완료 후 아래를 모두 만족하는지 확인합니다.

- [ ] 9섹션이 모두 있고, 비어 있는 섹션이 없다
- [ ] 색은 **시적 이름**과 **HEX** 모두 있다 (그냥 "파랑" ❌)
- [ ] 폰트 스케일이 7단계 이상 정의돼 있다
- [ ] Button의 4개 상태(Default/Hover/Focus/Disabled)가 모두 서술됐다
- [ ] Do·Don't 가 각 5개 이상이다
- [ ] Breakpoint 4개 모두 서술됐다
- [ ] 마지막에 Agent Prompt Guide 한 줄 요약이 있다

## 참고

원본: [google-labs-code/stitch-skills/design-md](https://github.com/google-labs-code/stitch-skills/tree/main/skills/design-md)
