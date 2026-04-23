---
name: taste-dials
description: AI 결과물의 디자인 감각을 3개의 숫자 다이얼(1–10)로 정밀 조절. DESIGN_VARIANCE, MOTION_INTENSITY, VISUAL_DENSITY — 요청 앞에 한 줄만 붙이면 전혀 다른 결과.
source: Leonxlnx/taste-skill
language: ko
---

# 04. taste-dials — 감각 다이얼

## 한 줄 사용법

프롬프트 맨 앞에 이 한 줄을 붙이세요.

```text
DIALS: VARIANCE=7, MOTION=5, DENSITY=4
```

같은 요청이라도 다이얼에 따라 결과가 극적으로 달라집니다.

## 다이얼 ①: DESIGN_VARIANCE (디자인 변주)

> **레이아웃의 파격 정도.** 낮으면 전통적이고 안전, 높으면 실험적이고 비대칭.

| 값 | 분위기 | 특징 |
|---|---|---|
| **1–3** | Clean / Centered | 중앙 정렬, 대칭, 교과서 레이아웃. 학부모 공식 안내에 추천 |
| **4–6** | Modern / Balanced | 약간의 비대칭, 섹션 간 리듬감. **기본값 권장** |
| **7–8** | Asymmetric / Editorial | 큰 여백, 매거진 레이아웃, 겹침 효과 |
| **9–10** | Experimental / Broken Grid | 극단적 비대칭, 타이포 오버플로, 스크롤 히어로 |

**교사용 가이드**
- 학부모·공식 문서 → 1–3
- 학급 홍보·학생 포트폴리오 → 5–6
- 동아리·축제·수상작 → 7–8

## 다이얼 ②: MOTION_INTENSITY (모션 강도)

> **애니메이션·인터랙션의 활발함.** 낮으면 정적, 높으면 화려.

| 값 | 분위기 | 기법 |
|---|---|---|
| **1–3** | Simple Hover | 버튼 색 변화, opacity 페이드 |
| **4–6** | Subtle Entrance | 스크롤 시 fade-up 0.6s, 카드 hover 상승 |
| **7–8** | Magnetic / Springy | 마우스 자석 효과, 탄성 스프링, 패럴랙스 |
| **9–10** | Cinematic / Scroll-driven | GSAP Scrollytelling, 3D, 루프 비디오 배경 |

**교사용 가이드**
- 공식 문서 → 1–3 (방해 금지)
- 학습 앱 → 3–5 (집중)
- 학급 홍보 → 5–6
- 축제·동아리 → 7+

## 다이얼 ③: VISUAL_DENSITY (시각 밀도)

> **정보량과 여백 비율.** 낮으면 고급스럽고 비어 있는 느낌, 높으면 대시보드처럼 빼곡.

| 값 | 분위기 | 특징 |
|---|---|---|
| **1–3** | Spacious / Luxury | 섹션 간 160px+, 한 화면에 1–2요소 |
| **4–6** | Balanced | 섹션 간 80–120px, 3–4요소 |
| **7–8** | Rich / Editorial | 섹션 간 60px, 카드 4–6개 그리드 |
| **9–10** | Dense Dashboard | 여백 최소, 정보 밀집 (출결표·성적표) |

**교사용 가이드**
- 랜딩·홍보 → 2–4
- 수업 안내 → 5–6
- 출결·성적·시간표 → 7–9

## 조합 레시피

바로 쓸 수 있는 검증된 조합입니다.

```text
# 학부모 공식 안내 (차분·정적·여백)
DIALS: VARIANCE=2, MOTION=2, DENSITY=3

# 학급 홍보 페이지 (권장 기본)
DIALS: VARIANCE=5, MOTION=4, DENSITY=4

# 학생 포트폴리오 (감각적)
DIALS: VARIANCE=7, MOTION=6, DENSITY=4

# 출결·성적 대시보드 (정보 밀집)
DIALS: VARIANCE=3, MOTION=2, DENSITY=8

# 축제·동아리 모집 (화려)
DIALS: VARIANCE=8, MOTION=8, DENSITY=5

# 퀴즈·게임 앱 (활발)
DIALS: VARIANCE=6, MOTION=7, DENSITY=5
```

## 동작 방식

AI는 다이얼 값을 아래 CSS 변수와 Tailwind 클래스로 변환합니다.

```css
/* VARIANCE=5 예시 */
--layout-offset: 24px;       /* 2라면 0px, 10이라면 120px */
--grid-asymmetry: 0.3;       /* 2면 0, 10이면 0.9 */

/* MOTION=5 예시 */
--transition-base: 0.35s;    /* 2면 0.15s, 10이면 0.9s */
--hover-lift: 4px;           /* 2면 0px, 10이면 12px */

/* DENSITY=5 예시 */
--section-gap: 96px;         /* 2면 160px, 10이면 32px */
--card-padding: 24px;        /* 2면 48px, 10이면 12px */
```

## 사용 예시

```text
사용자: "우리 반 페이지 만들어줘. 학부모도 보는 공식 페이지야"
↓
AI 내부: DIALS: VARIANCE=3, MOTION=3, DENSITY=4 자동 설정
↓
결과: 중앙 정렬, 차분한 페이드, 넉넉한 여백의 안정적 페이지
```

```text
사용자: "예술 동아리 모집 페이지, 감각 있게!"
↓
AI 내부: DIALS: VARIANCE=8, MOTION=7, DENSITY=5 자동 설정
↓
결과: 매거진 레이아웃, 자석 hover, 패럴랙스, 감각적 편집 디자인
```

## 참고

원본: [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
