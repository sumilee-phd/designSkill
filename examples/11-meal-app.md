# 예제 11 — 급식앱 🍱

> **시나리오**: 학생·학부모가 오늘·이번 주 급식을 확인하고, 영양·알레르기를 체크하고, 별점을 남기는 4-탭 모바일 앱
> **소요 시간**: 60–90분
> **난이도**: ⭐⭐⭐ 고급 (데이터 구조 + 필터 + 탭 내비 + 프로필)
> **업데이트**: 2026.05 · Bistro 프리셋 적용 · 4-탭 내비 구조 · 프로필 기능 추가

## 🎨 디자인 프리셋 선택

| 프리셋 | 분위기 | 적합 맥락 |
|---|---|---|
| [`meal-bistro`](../presets/education/meal-bistro.md) ⭐ **권장** | 크림+올리브 에디토리얼 · 셰프 큐레이션 | 중·고등·교직원 식당 |
| [`classroom-pastel`](../presets/education/classroom-pastel.md) | 따뜻한 파스텔 · 친근 | 초등 저·중학년 |
| [`lesson-clean`](../presets/education/lesson-clean.md) | 정돈된 딥블루 | 자료 중심 · 학부모 공식 |

> **권장**: 대부분의 학교 급식앱은 `meal-bistro` 프리셋이 가장 적합. 음식 사진이 주인공이 되는 에디토리얼 감성이 식욕을 자극하고 프리미엄 인상을 줍니다.

## 🗺️ 4-탭 앱 구조 (하단 내비)

```
┌─────────┬─────────┬─────────┬─────────┐
│  🏠 홈  │ 🍽️ 메뉴 │ ⭐ 후기 │ 👤 프로필│
└─────────┴─────────┴─────────┴─────────┘
```

| 탭 | 역할 | 핵심 기능 |
|---|---|---|
| **홈** | 오늘의 대표 메뉴 · 퀵 액션 | Hero + 주간 식단 바로가기 + 문의 |
| **메뉴** | 주간 식단표 · 일자별 상세 | 요일 탭 · 4카테고리 그리드 · 영양 정보 |
| **후기** | 학생 별점 · 한 줄 감상 | 별점 입력 · 실시간 타임라인 |
| **프로필** | 내 알레르기 · 알림 설정 | 18개 알레르기 프로필 · TTS · 큰 글씨 |

## 📱 화면별 상세 설계

### 화면 ① 홈 (씨마스고등학교 · 앱 진입 첫 화면)

```
🏫 씨마스고등학교            🔔 🔍
────────────────────────────────
[ 세로형 Hero 카드 · 4:5 비율 ]
    치즈돈까스 사진 (전면)
    ┌──────────────────┐
    │  🏷️ CHEF'S PICK   │
    │                  │
    │ SPECIAL MENU     │
    │ 2026년 5월 21일   │
    │ (목) 오늘의 메뉴  │
    │ 🍽️ 치즈돈까스 정식 │
    └──────────────────┘

┌──────────┬──────────┐
│ 📅 주간    │ 💬 문의·  │
│  식단      │  피드백   │
│ 한 주간의  │ 더 맛있는  │
│ 즐거운 소식 │ 식탁을 위해│
└──────────┴──────────┘

────── 하단 탭 ──────
[🏠 홈] [🍽️ 메뉴] [⭐ 후기] [👤 프로필]
       ●
```

### 화면 ② 메뉴 (주간 + 일자별 상세)

#### 상단: 주간 선택
```
씨마스고등학교            📅 🔔
────────────────────────────────
WEEKLY SELECTION
5월 넷째 주 식단표        [셰프 일러스트]
May 18 – May 22, 2026

MON  TUE  WED  THU  FRI
 18   19   20  [21]  22
              ●(액티브)
```

#### 중단: Hero 카드 (선택된 날짜의 대표 메뉴)
```
┌──────────────────────┐
│ [음식 사진 4:5]        │
│   CHEF'S PICK 라벨     │
│                      │
│  🍽️                  │
│  오늘의 메인    845    │
│  치즈돈까스     kcal   │
│                      │
│  ● 백미밥  ● 어니언스프 │
└──────────────────────┘
```

#### 하단: 4-카테고리 그리드 (상세)
```
TODAY'S MENU
2026년 5월 21일 (목)

[큰 음식 사진 3:4 · MAIN COURSE · 치즈돈까스]

┌──────────┬──────────┐
│ 🌾 STAPLE │ 🥣 SOUP  │
│  백미밥    │ 어니언스프 │
├──────────┼──────────┤
│ 🥗 SIDE   │ 🥬 TRAD. │
│발사믹샐러드 │ 배추김치  │
└──────────┴──────────┘

### 영양 정보
┌─────────┬─────────┐
│ 🔥 685  │ 🥩 42g  │
│ CALORIES│ PROTEIN │
├─────────┼─────────┤
│ 🌾 82g  │ 💧 650mg│
│ CARBS   │ SODIUM  │
└─────────┴─────────┘

### 알레르기 포함
⚠️ 대두 · 우유 · 밀 · 돼지고기 · 난류
```

### 화면 ③ 후기 (학생 평가)

```
╭─────────────────────╮
│   🌟 오늘 급식은?    │
│   어땠나요?          │
│   ⭐⭐⭐⭐⭐         │
│                     │
│   한 줄 감상 (선택)   │
│   [_________________]│
│                     │
│   [등록하기]         │
╰─────────────────────╯

────── 실시간 친구들 후기 ──────
🐻 지혜로운 부엉이          방금 전
⭐⭐⭐⭐⭐
"오늘 스파게티 소스가 진짜 맛있었어요!
 내일 급식도 기대돼요."

🦊 꼼꼼한 여우             10분 전
⭐⭐⭐⭐☆
"치즈돈까스 최고! 양만 조금 더..."
```

### 화면 ④ 프로필 (알레르기 · 접근성)

```
👤 내 정보
────────
별명: 지혜로운 부엉이 🐻 [변경]
학년·반: 2학년 3반

### 내 알레르기 프로필 (선택)
주의해야 할 재료를 선택해주세요
선택한 알레르기가 포함된 메뉴는 자동으로 강조됩니다.

┌─────┬─────┬─────┐
│ 🥚  │ 🥛  │ 🌾  │
│ 난류 │ 우유 │ 메밀 │
├─────┼─────┼─────┤
│ 🥜  │ 🌱  │ 🐟  │
│ 땅콩 │ 대두 │고등어│
├─────┼─────┼─────┤
│ 🦀  │ 🦐  │ 🐖  │
│  게 │ 새우 │돼지고기│
├─────┼─────┼─────┤
│ 🍑  │ 🍅  │ 🌰  │
│ 복숭아│ 토마토│ 호두 │
├─────┼─────┼─────┤
│ 🐔  │ 🐂  │ 🦑  │
│ 닭고기│쇠고기 │오징어│
├─────┼─────┼─────┤
│ 🐚  │ 📄  │     │
│조개류 │아황산염│     │
└─────┴─────┴─────┘
     18개 중 2개 선택됨

[ 💾 안전하게 저장하기 ]

### 접근성
🔊 메뉴 읽어주기 (TTS)       [ON/OFF]
🔍 큰 글씨 모드               [ON/OFF]
🌙 다크 모드                  [자동/수동]

### 알림
📬 내일 메뉴 미리보기 알림     [OFF]
⚠️ 내 알레르기 포함 메뉴 경고  [ON]
```

## 🏗️ 프롬프트 (Stitch → AI Studio Build)

````text
@SKILL.md
@presets/education/meal-bistro.md
DIALS: VARIANCE=5, MOTION=3, DENSITY=6

# 프로젝트: 씨마스고등학교 급식앱 (4-탭 모바일)

## 목표
학생·학부모가 오늘·이번 주 급식을 확인하고 알레르기 필터·별점 평가까지
가능한 4-탭 하단 내비 모바일 앱.

## 화면 구조
1. **홈 탭** — Hero 카드 (오늘 대표 메뉴 · CHEF'S PICK) + 2카드 퀵 액션 (주간 / 문의)
2. **메뉴 탭** — 주간 WEEKLY SELECTION · 요일 day-tabs · 선택일 상세 (4카테고리 그리드 + 영양 + 알레르기)
3. **후기 탭** — 별점 입력 · 한 줄 감상 · 실시간 친구들 후기 타임라인
4. **프로필 탭** — 별명·학급 · 18 알레르기 선택 · 접근성 토글 (TTS·큰글씨·다크) · 알림 설정

## 디자인 규칙
- meal-bistro 프리셋 토큰 그대로 사용 (크림 #F5E9C8 + 올리브 #5A6B3E)
- 영문 레이블은 uppercase + letter-spacing 0.14em
  - "CHEF'S PICK", "WEEKLY SELECTION", "TODAY'S MENU", "MAIN COURSE", "STAPLE", "SOUP", "SIDE", "TRADITIONAL"
- 음식 사진이 Hero 주인공 (화면 40-60% 점유)
- 라운드: Hero 24px · 카드 16px · 배지 4px · 태그 8px
- 하단 고정 탭 네비 (Safe Area 대응)
- 다크 모드 필수

## 데이터
- public/meals.json (2주치 · 10일)
- constants/allergens.ts (18개 법정)
- LocalStorage: 알레르기 프로필 · 별점 이력 · 설정

## 기술 스택
- 단일 HTML (Tailwind CDN) — 간단 버전
- 또는 Vite + React + TypeScript + Tailwind — 확장 버전

## 접근성
- 알레르기 경고 = 색 + 텍스트 + 아이콘 3중 (색맹 고려)
- TTS 지원 (SpeechSynthesis API)
- 큰 글씨 모드 토글
- 터치 타깃 48×48 이상
- Safe Area 상/하단 반영
````

## 📦 데이터 구조 (meals.json)

```json
{
  "2026-05-21": {
    "dayOfWeek": "목",
    "isChefsPick": true,
    "photo": "/images/meals/2026-05-21.jpg",
    "photoAlt": "치즈돈까스와 백미밥, 어니언스프, 발사믹샐러드, 배추김치",
    "mainDish": {
      "name": "치즈돈까스",
      "nameEn": "Cheese Pork Cutlet",
      "category": "MAIN COURSE"
    },
    "menu": {
      "staple": { "name": "백미밥", "nameEn": "Steamed Rice" },
      "soup":   { "name": "어니언스프", "nameEn": "Onion Soup" },
      "side":   { "name": "발사믹샐러드", "nameEn": "Balsamic Salad" },
      "traditional": { "name": "배추김치", "nameEn": "Kimchi" }
    },
    "nutrition": {
      "calories": 685,
      "protein": 42,
      "carbs": 82,
      "fat": 24,
      "sodium": 650,
      "dailyRatio": {
        "calories": 97,
        "protein": 105,
        "carbs": 68,
        "fat": 80
      }
    },
    "allergens": ["대두", "우유", "밀", "돼지고기", "난류"],
    "origin": {
      "돼지고기": "국내산",
      "쌀": "국내산",
      "배추": "국내산 (강원)",
      "치즈": "수입산 (덴마크)"
    },
    "nutritionistNote": "치즈돈까스는 학생 인기 메뉴! 채소 샐러드와 함께 균형 있게 드세요."
  }
}
```

## 🏷️ 18개 법정 알레르기 상수 (constants/allergens.ts)

```ts
export const ALLERGENS = [
  { id: 'egg',       name: '난류',     nameShort: '난류',     icon: '🥚', emoji: '🥚' },
  { id: 'milk',      name: '우유',     nameShort: '우유',     icon: '🥛', emoji: '🥛' },
  { id: 'buckwheat', name: '메밀',     nameShort: '메밀',     icon: '🌾', emoji: '🌾' },
  { id: 'peanut',    name: '땅콩',     nameShort: '땅콩',     icon: '🥜', emoji: '🥜' },
  { id: 'soybean',   name: '대두',     nameShort: '대두',     icon: '🌱', emoji: '🌱' },
  { id: 'wheat',     name: '밀',       nameShort: '밀',       icon: '🌾', emoji: '🌾' },
  { id: 'mackerel',  name: '고등어',   nameShort: '고등어',   icon: '🐟', emoji: '🐟' },
  { id: 'crab',      name: '게',       nameShort: '게',       icon: '🦀', emoji: '🦀' },
  { id: 'shrimp',    name: '새우',     nameShort: '새우',     icon: '🦐', emoji: '🦐' },
  { id: 'pork',      name: '돼지고기', nameShort: '돼지고기', icon: '🐖', emoji: '🐖' },
  { id: 'peach',     name: '복숭아',   nameShort: '복숭아',   icon: '🍑', emoji: '🍑' },
  { id: 'tomato',    name: '토마토',   nameShort: '토마토',   icon: '🍅', emoji: '🍅' },
  { id: 'sulfite',   name: '아황산염', nameShort: '아황산염', icon: '📄', emoji: '📄' },
  { id: 'walnut',    name: '호두',     nameShort: '호두',     icon: '🌰', emoji: '🌰' },
  { id: 'chicken',   name: '닭고기',   nameShort: '닭고기',   icon: '🐔', emoji: '🐔' },
  { id: 'beef',      name: '쇠고기',   nameShort: '쇠고기',   icon: '🐂', emoji: '🐂' },
  { id: 'squid',     name: '오징어',   nameShort: '오징어',   icon: '🦑', emoji: '🦑' },
  { id: 'shellfish', name: '조개류',   nameShort: '조개류',   icon: '🐚', emoji: '🐚' },
] as const;
```

## 🔍 기능 점검 체크리스트

### ✅ 기본 기능 (1차 구현)
- [ ] 홈 · 메뉴 · 후기 · 프로필 4-탭 내비 동작
- [ ] meals.json 로드 & 오늘 날짜 자동 선택
- [ ] 요일 탭(월~금) 클릭 시 화면 갱신
- [ ] 4-카테고리 그리드 렌더
- [ ] 영양 정보 4개 숫자 카드
- [ ] 알레르기 배지 노출 (해당 원료만)

### ⚙️ 상호작용 (2차)
- [ ] 별점 UI — 탭하면 점등, LocalStorage에 저장
- [ ] 한 줄 감상 입력 (140자 제한)
- [ ] 후기 타임라인 렌더 (최근 10건)
- [ ] 알레르기 프로필 선택 & 저장
- [ ] "내 알레르기 포함" 메뉴는 메뉴 화면에서 테라코타 테두리로 경고
- [ ] TTS 읽어주기 (`SpeechSynthesis` API)

### 🌐 외부 연동 (3차 · 선택)
- [ ] NEIS Open API 연동 (실제 급식 데이터)
- [ ] Google Sheets 백엔드 (영양교사가 스프레드시트로 관리)
- [ ] QR 코드 생성 (학부모 공유용)
- [ ] 카카오톡 공유 (카카오 Share SDK)
- [ ] PWA 설치 (`manifest.json` + service worker)

### 🎨 디자인 검수
- [ ] Hero 사진 화면 40-60% 점유
- [ ] 영문 레이블 uppercase + letter-spacing 0.14em
- [ ] 라운드 일관 (24/16/8/4)
- [ ] 올리브 그린은 CTA·배지에만 (10-15% 이하)
- [ ] 다크 모드 지원 (자동 감지 `prefers-color-scheme`)
- [ ] Safe Area 상·하단 반영

### ♿ 접근성
- [ ] 알레르기 경고 = 색 + 텍스트 + 아이콘 3중
- [ ] 모든 `<img>`에 의미 있는 alt
- [ ] 터치 타깃 48×48 이상
- [ ] 키보드 내비게이션 지원
- [ ] 색 대비 WCAG AA (크림 배경 #F5E9C8 + 잉크 텍스트 #2C2818 대비 확인)
- [ ] `prefers-reduced-motion` 대응

## 🚀 AI Studio Build 3단계 이식 프롬프트

### 1단계: 구조 + 디자인 (라우팅만)
```text
다음 4-탭 모바일 앱 UI를 React + TypeScript + Tailwind로 이식.
디자인(크림 #F5E9C8 + 올리브 #5A6B3E)과 meal-bistro 프리셋 토큰을 그대로 유지.

## Stitch HTML
[Stitch로 만든 4개 화면 붙여넣기]

## 이번 단계
- react-router-dom으로 4탭 라우팅 (/home, /menu, /review, /profile)
- 하단 탭 네비 컴포넌트 (BottomNav)
- meals.json을 public/에 배치하고 useEffect로 로드
- 기능은 아직 넣지 말고 디자인만 정확히
```

### 2단계: 상호작용 (필터 + 별점)
```text
이제 상호작용을 추가.

1. 프로필 탭의 18 알레르기 선택 → LocalStorage에 저장
2. 메뉴 탭에서 내 알레르기 포함 메뉴는 테라코타 #B54734 테두리 2px
3. 후기 탭의 별점 → LocalStorage에 날짜별 저장
4. 한 줄 감상은 140자 제한, 빈 값 허용
5. 실시간 친구들 후기는 LocalStorage의 최근 10건 렌더 (익명 별명 랜덤)
```

### 3단계: 고급 기능 (선택)
```text
마무리 기능.

1. TTS 읽어주기 (SpeechSynthesis API)
2. 큰 글씨 모드 토글 (html class 기반)
3. 다크 모드 (자동 + 수동 전환)
4. PWA manifest + 기본 아이콘
5. 메뉴 탭에 "카카오톡 공유" 버튼 (카카오 SDK)
```

## 🎯 4회차 연수 활용

이 예제를 공통 과제로 선택 시:

| 단계 | 소요 | 내용 |
|---|---|---|
| ③ AI Studio 명세 | 15분 | 위 화면 구조 기반 정리 |
| ④ Stitch 화면 | 25분 | 4개 화면 각각 생성 (meal-bistro 프리셋) |
| ⑤ 멀티페이지 | 20분 | DESIGN.md 추출 · 일관성 확인 |
| ⑥ AI Studio Build | 25분 | 위 3단계 이식 프롬프트 |
| ⑦ GitHub · ⑧ Vercel | 30분 | 배포 |

## ⚠️ 주의 사항

- **개인정보**: 학생 실명·사진·학번 사용 금지. 별점·감상은 **별명** 또는 익명
- **알레르기 면책**: 하단 작게 "본 앱의 알레르기 정보는 영양교사가 제공한 자료 기준. 개인 알레르기 증상은 의료진 확인 필요" 명시
- **이미지 저작권**: 급식 사진은 직접 촬영 또는 Unsplash / Pexels의 CC0 사진만
- **상업적 표현 금지**: 광고·프로모션 느낌 배제. "Chef's Pick"은 큐레이션 의미로만 사용

## 📚 참고 자료

- [교육부 학교 알레르기 유발 식품 18종 고시](https://www.moe.go.kr/)
- [NEIS Open API 포털](https://open.neis.go.kr/)
- [meal-bistro 프리셋](../presets/education/meal-bistro.md)
- [designSkill 03-korean-style](../skills/03-korean-style/SKILL.md)
- [designSkill 15-ai-studio-build](../skills/15-ai-studio-build/SKILL.md)

## 🔗 관련 예제

- [03-parent-guide](./03-parent-guide.md) — 급식앱을 학부모 안내 앱에 통합
- [10-subject-hub](./10-subject-hub.md) — 학교 정보 허브 편입
- [05-attendance](./05-attendance.md) — 교사 전용 페이지 UX 참고
