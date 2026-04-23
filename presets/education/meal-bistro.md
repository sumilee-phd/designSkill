# 급식 비스트로 에디토리얼 스타일 🍱

> **연수 오리지널 · 중·고등 급식앱 · 카페테리아 · 교직원 식당 · 편집자 큐레이션 감성**

## 1. Visual Theme & Atmosphere
- **무드**: 에디터가 큐레이션한 셰프 레스토랑 메뉴판. 음식이 주인공, 디자인은 플레이팅.
- **키워드**: 크림 · 올리브 · 셰프 · 정갈 · 따스한 미식 · 무광 고급감
- **철학**: "학교 급식을 '미식'의 언어로 바라본다."

## 2. Color Palette & Roles

```
━━ 메인 팔레트 (크림·올리브) ━━
```

- 크림 베이지 `#F5E9C8` — **Background** (주요 배경 · 따뜻한 오프화이트)
- 라이트 크림 `#FAF3DC` — Surface (카드 기본)
- 아이보리 화이트 `#FFFDF5` — Elevated Surface (모달·오버레이)
- 크림 워머 `#EEDFB2` — Surface Inset (구분 섹션)

```
━━ 악센트 (올리브 그린) ━━
```

- 올리브 그린 `#5A6B3E` — **Primary** (CTA · 액티브 탭 · 배지)
- 다크 올리브 `#3E4A2C` — Text Strong · Primary Hover
- 미드 올리브 `#7C8E5A` — Secondary
- 페일 올리브 `#A8B88C` — Accent Soft (진행 바 · 미사용 상태)

```
━━ 보조 ━━
```

- 워밍 브라운 `#8B6F47` — 사진 배경 · 우드 접시
- 잉크 `#2C2818` — Text Primary
- 머니 브라운 `#6B6045` — Text Secondary
- 미드 그레이 `#9A9074` — Text Tertiary · 메타
- 라인 `#D9CDA8` — Border

```
━━ 상태 ━━
```

- 성공 `#5A6B3E` (올리브 재사용 — 일관성)
- 경고 `#D4923A` (토스트 앰버)
- 위험 `#B54734` (테라코타 — 알레르기 경고)
- 정보 `#7C8E5A` (미드 올리브)

## 3. Typography Rules

- **한국어 기본**: Pretendard Variable
- **영문 레이블**: `font-variant: all-small-caps` 또는 수동 `uppercase` + `letter-spacing: 0.14em`
  - 예: "WEEKLY SELECTION", "TODAY'S MENU", "CHEF'S PICK", "MAIN COURSE"
- **숫자 (kcal·영양소)**: `font-variant-numeric: tabular-nums; font-weight: 900;`

### 스케일
| 용도 | 크기 | 굵기 | letter-spacing |
|---|---|---|---|
| Display (큰 날짜) | 32–40px | 900 | -0.025em |
| H1 (섹션 제목) | 24–28px | 800 | -0.025em |
| H2 | 20px | 800 | -0.02em |
| H3 | 17px | 700 | -0.015em |
| Body | 15px | 500 | -0.005em |
| Label EN | 11–12px | 700 | **0.14em** |
| Small | 13px | 600 | 0 |
| Micro/Meta | 11px | 600 | 0.02em |

### line-height
- 제목 1.25
- 본문 1.6
- Label EN 1.1

## 4. Component Stylings

### Hero Image Card
```css
border-radius: 24px;
overflow: hidden;
position: relative;
aspect-ratio: 4 / 5;
/* 하단 그라디언트 오버레이로 제목 가독성 확보 */
background: 
  linear-gradient(to top, rgba(44,40,24,0.85) 0%, transparent 45%),
  url('...') center/cover;
```
- 상단: `CHEF'S PICK` 올리브 배지 (`#5A6B3E` 배경 + 흰 텍스트 + 둥근 모서리 4px)
- 하단: 큰 날짜 + 대표 메뉴 이름 (흰 텍스트 + 그림자)

### Day Tab (주간 선택)
```
MON TUE WED THU FRI
 18  19  20  21  22
          ●(active)
```
- 각 요일 폭 48px, 세로 중앙정렬
- 영문 요일 (uppercase · 12px · 머니 브라운)
- 숫자 (20px · 검정)
- 액티브: 숫자 주위 32px 원형 `#5A6B3E` 배경 + 흰 숫자

### Category Card (4분할 그리드)
```
┌─────────┬─────────┐
│ 🌾 STAPLE│ 🥣 SOUP  │
│  백미밥   │ 어니언스프 │
├─────────┼─────────┤
│ 🥗 SIDE  │ 🥬 TRAD. │
│발사믹샐러드│ 배추김치  │
└─────────┴─────────┘
```
- 크림 배경 + 라운드 16px
- 좌상단 24×24 올리브 아이콘
- 그 옆 영문 레이블 (uppercase 11px · 페일 올리브)
- 그 아래 한국어 메뉴명 (17px · 800 · 다크 올리브)
- padding: 16px

### Chef Badge
```html
<span class="inline-flex items-center gap-1 px-2.5 py-1 rounded-md 
             bg-[#5A6B3E] text-white text-[11px] font-bold uppercase tracking-[0.14em]">
  Chef's Pick
</span>
```

### Nutrition Chip (영양소 카드)
```html
<div class="rounded-xl bg-[#FAF3DC] p-4 border border-[#D9CDA8]">
  <div class="flex items-center gap-1 text-[#7C8E5A]">
    <iconify-icon icon="solar:fire-bold-duotone" width="16"></iconify-icon>
    <span class="text-[11px] uppercase tracking-[0.14em] font-bold">Calories</span>
  </div>
  <div class="mt-1 text-[#2C2818] font-black tabular-nums">
    <span class="text-3xl">685</span>
    <span class="text-sm ml-1">kcal</span>
  </div>
</div>
```

### Bottom Navigation (하단 탭)
- 3–4개 탭 · 고정 하단 64px
- 배경: `rgba(250,243,220,0.95)` + backdrop-blur
- 상단 얇은 라인 `#D9CDA8`
- 아이콘 24×24 · 액티브는 32×32 원형 올리브 배경 + 흰 아이콘
- 레이블 11px · 액티브는 다크 올리브, 비액티브는 머니 브라운
- Safe area 대응: `padding-bottom: env(safe-area-inset-bottom);`

### Allergy Icon Grid
- 6행 3열 그리드 (18개 법정 알레르기)
- 각 셀: 라운드 12px · 배경 크림 워머 · 아이콘(이모지 or Iconify) + 이름
- 내 알레르기 선택 시: 올리브 그린 테두리 2px + 체크 마크
- 위험 상태: 테라코타 `#B54734` 테두리 + 경고 아이콘

### Rating Stars
- 별 5개 · 각 36px (터치 타깃 확보)
- 액티브: 올리브 그린, 비활성: 페이지 그린 (10% opacity)

## 5. Layout Principles

- **모바일 우선**: 430px 폭 기준 설계
- **Safe Area**: 상단·하단 `env(safe-area-inset)` 필수 반영
- **섹션 패딩**: 좌우 20px · 상하 24–32px
- **카드 간격**: 12–16px
- **Hero 비율**: 4:5 (세로형) — 음식 사진 기준
- **최대 폭**: 450px (태블릿 이상에서 중앙 정렬)

### 디바이스 대응
- `< 430px`: 단일 컬럼, 모든 카드 풀 와이드
- `430–768px`: 여전히 단일 컬럼, 좌우 여백 확대
- `768px+`: 카드 2열 그리드 (데스크톱은 웹앱 감성 유지)

## 6. Depth & Elevation

- **L0 플랫**: 크림 바탕 + 얇은 라인으로 구분
- **L1 기본**: `box-shadow: 0 4px 12px rgba(60,50,30,0.06);` — 카드 기본
- **L2 강조**: `box-shadow: 0 12px 32px rgba(60,50,30,0.12);` — 호버 · 모달
- **L3 셰프 픽**: `box-shadow: 0 16px 40px rgba(90,107,62,0.18);` — Hero 특별 강조

사진은 그림자 대신 **라운드 + 내부 오버레이**로 처리 (플레이팅 감성).

## 7. Do's and Don'ts

✅ **Do**
- 음식 사진을 **Hero의 주인공**으로 (화면의 40–60% 점유)
- 영문 uppercase 레이블 + 한국어 큰 본문 조합 (에디토리얼 감각)
- 올리브 그린은 **악센트 10–15%만** 사용 (CTA · 액티브 탭 · 배지)
- 여백을 넉넉히 (접시 주변 여백 같은 플레이팅 감성)
- 라운드는 일관되게 (카드 16, Hero 24, 배지 4, 태그 8)

❌ **Don't**
- 파스텔 다색상 금지 (이 프리셋은 **크림 단색 + 올리브 1악센트**만)
- 글로스 · 네온 · 그라디언트 과다 (무광 고급감 유지)
- 과도한 이모지 (배지·아이콘은 OK, 본문에 ❤️🔥🎉 삽입 금지)
- 화려한 애니메이션 (fade in/out 외에는 자제)
- 라이트 모드만 전제 — **다크 모드도 필수 대응**

## 8. Responsive Behavior

- 모바일 우선 (430px)
- 하단 탭 내비는 **모바일에만** 노출, 태블릿 이상은 상단 탭으로 전환
- 터치 타깃 **최소 48×48**
- 가로 모드(landscape)에서는 Hero 높이 자동 축소

### Safe Area
```css
/* iOS 노치·인디케이터 대응 */
body {
  padding-top: env(safe-area-inset-top);
  padding-bottom: calc(64px + env(safe-area-inset-bottom));
}
```

## 9. Agent Prompt Guide

> "급식 비스트로 스타일: Pretendard + uppercase 영문 레이블 · 크림 베이지 `#F5E9C8` 배경 · 올리브 그린 `#5A6B3E` 악센트 · 라운드 24px Hero 사진 · CHEF'S PICK 배지 · 4카테고리 그리드 (STAPLE/SOUP/SIDE/TRADITIONAL) · 하단 탭 네비 3–4개 · 무광 플레이팅 감성 · 이모지 최소 사용."

## 🌙 다크 모드 토큰

```css
[data-theme="dark"] {
  --bg: #2A2617;           /* 다크 올리브 인크 */
  --surface: #3E3A28;
  --surface-warm: #4C4631;
  --text: #F5E9C8;         /* 본문은 크림 */
  --text-strong: #FFFDF5;
  --muted: #C9BC97;
  --border: #5C5236;
  --primary: #9CAE78;      /* 더 밝은 올리브 */
  --primary-hover: #B6C892;
}
```

## 🏫 활용 예시

- 중·고등학교 급식앱 (`examples/11-meal-app.md`)
- 기숙사·교직원 식당 메뉴
- 교내 매점·협동조합 앱
- 학교 축제 음식 부스 안내
- 조리실습실 · 가정 교과 실습 기록

## 🎨 마이크로카피 예시

```text
[홈]
Hero kicker: "SPECIAL MENU"
Main: "2026년 5월 21일 (목) 오늘의 메뉴"
Primary dish: "치즈돈까스 정식"

[주간]
Kicker: "WEEKLY SELECTION"
Title: "5월 넷째 주 식단표"
Range: "May 18 – May 22, 2026"
Badge: "CHEF'S PICK"

[메뉴 상세]
Kicker: "TODAY'S MENU"
Category labels: "MAIN COURSE" · "STAPLE" · "SOUP" · "SIDE" · "TRADITIONAL"

[CTA]
"주간 식단 보기" · "문의 · 피드백" · "내 알레르기 설정"
```

## 관련 스킬

- [01-design-md](../../skills/01-design-md/SKILL.md) — 이 프리셋에서 DESIGN.md 생성
- [03-korean-style](../../skills/03-korean-style/SKILL.md) — 한국어 최적화 기본
- [examples/11-meal-app](../../examples/11-meal-app.md) — 급식앱 예제 (이 프리셋 활용)
