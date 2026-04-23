---
name: redesign
description: 기존 UI를 분석해 단계적으로 개선. 이전과 이후를 비교하고, 변경 이유와 적용된 디자인 원칙을 명확히 설명.
source: Leonxlnx/taste-skill
language: ko
---

# 08. redesign — 기존 UI 개선

## 언제 사용하나

- 작년 만든 학급 페이지를 **올해 다시 다듬고** 싶을 때
- 선배 교사가 만든 페이지를 **세련되게 업데이트**할 때
- 너무 옛날 느낌의 학교 홈페이지를 **현대화**할 때
- 학생 작품을 **보완 · 첨삭 교육** 목적으로 리디자인할 때

## 5단계 리디자인 프로세스

### ① 진단 (Diagnose)
기존 HTML/스크린샷을 받아 아래 체크리스트로 점수화:

- [ ] 타이포그래피: 한국어 최적화? Pretendard? 줄바꿈?
- [ ] 색 팔레트: 명확한 역할 구분? 대비 AA?
- [ ] 레이아웃: 모바일 반응형? 여백 일관성?
- [ ] 컴포넌트: 상태별(hover/focus/disabled) 처리?
- [ ] 모션: 불필요한 애니메이션? 접근성?
- [ ] 접근성: 포커스 링? alt 텍스트? 키보드 탐색?
- [ ] 콘텐츠: 플레이스홀더 잔존? 영어 번역투?

각 항목 1–5점 → **총점 35점 만점** 보고.

### ② 우선순위 제안 (Prioritize)
개선 항목을 **Impact × Effort** 매트릭스에 배치:

```
    효과 ↑
High│ [QUICK WINS]     [BIG BETS]
    │ 먼저 할 일         계획적 투자
    │
Low │ [NICE TO HAVE]   [AVOID]
    │ 여유 시 처리       넘기기
    └──────────────────────→ 노력
         Low         High
```

### ③ 디자인 토큰 재정의 (Tokens)
`skills/01-design-md/SKILL.md` 를 호출해 **새 DESIGN.md** 를 생성.
기존 코드에서 색·간격·폰트 값을 추출 → 의도에 맞게 정리.

### ④ 섹션별 리라이트 (Rewrite)
한 번에 페이지 전체를 갈아엎지 말고, **섹션 단위**로:

```markdown
## Section: Hero (Before → After)

### Before
- 회색 배경, 24px 제목, 영어 "Welcome to Class 4"
- CTA 2개가 같은 색, 시각 계층 없음

### After
- 따뜻한 파스텔 그라디언트, 48px 한국어 제목
- CTA 1개만 Primary (Filled), 나머지 Ghost
- 스크롤 시 fade-up 애니메이션 0.6s

### Why
- 한국어 타겟이므로 한국어 카피 우선
- Primary가 2개면 사용자가 선택 피로 (Hick's Law)
- 여백 확대로 고급감 강화
```

### ⑤ 차이점 문서화 (Diff Report)
최종 결과물과 함께 `REDESIGN_NOTES.md` 생성:
- 변경 항목 리스트 (섹션별)
- 각 변경의 이유 (디자인 원칙 + UX 근거)
- 제외한 변경 및 그 이유 (시간·범위)
- 다음 단계 제안

## 교사용 사례

### 사례: 작년 학급 페이지 리프레시

**Before**:
- 흰 배경 + 파란색 테두리 박스
- 제목 "2025 4학년 3반" (맑은고딕, 24px)
- 학생 사진 6장이 2줄 3열로 빽빽하게

**After 제안**:
- 복숭아→산호 그라디언트 Hero (따뜻한 학급 감성)
- 제목 "함께한 1년, 4학년 3반의 기록" (Pretendard 48px)
- 학생 작품을 가로 스크롤 갤러리로 — 사진 클릭 시 에세이 펼침

## 사용 방법

```text
사용자: @skills/08-redesign 로 이 페이지 개선 제안해줘
[기존 HTML 첨부 또는 스크린샷]

AI: [5단계 순차 실행 → Before/After + 근거 설명 출력]
```

## 참고

원본: [Leonxlnx/taste-skill — redesign-skill](https://github.com/Leonxlnx/taste-skill)
