# 예제 11 — 급식앱 🍱

> **시나리오**: 학생이 오늘·이번 주 급식을 확인하고, 영양 정보·알레르기를 체크하고, 별점을 남기는 급식 전용 앱
> **소요 시간**: 60–90분
> **난이도**: ⭐⭐⭐ 고급 (데이터 구조 + 필터링 + 반응형)

## 왜 이 예제인가

- 학생이 **매일 확인**하는 페이지 (재방문율 높음) → 다른 앱 배포·홍보 효과
- 학부모가 **알레르기 정보**를 쉽게 찾기 어려운 현실 해결
- 영양교사 업무 경감 (NEIS 데이터 자동 노출)
- 담임은 URL 공유만 → 별도 운영 부담 없음

## 3가지 사용자 시점

| 사용자 | 핵심 관심사 | 접근 빈도 |
|---|---|---|
| **학생** | 오늘·내일 뭐 먹어? 별점·감상 남기기 | 매일 1–2회 |
| **학부모** | 알레르기·나트륨·영양소 확인 | 주 2–3회 |
| **영양교사** | 메뉴 등록·학생 평가 확인 | 주 1–2회 |

## 프롬프트

````text
@SKILL.md
@presets/education/classroom-pastel.md  # 초등 · 친근
@presets/education/lesson-clean.md     # 중·고등 · 정돈 (선택)
@presets/korean/toss.md                # 영양 숫자 카드 감성 (부분 차용)
DIALS: VARIANCE=4, MOTION=4, DENSITY=6

# 프로젝트: 한강초 4학년 3반 급식앱

## 목적
학생·학부모가 오늘과 이번 주 급식 메뉴를 한눈에 확인하고,
알레르기 정보를 필터링하며, 별점으로 피드백을 남기는 데일리 웹앱.

## 페이지 구조 (단일 HTML 또는 React)

### 1. Hero (상단 고정 60vh)
- 오늘 날짜 + 요일 (크게, Pretendard Black 40px+)
- 대표 메뉴 사진 (4:3 비율, 라운드 20px)
- 대표 메뉴 이름 ("오늘의 점심: 제육볶음 + 미역국")
- 오늘 평균 별점 (★★★★☆ 4.3 / 5.0 · 참여 23명)
- 상단 CTA: "알레르기 체크" · "영양 정보 보기"

### 2. 오늘의 급식 상세 (카드 섹션)
4개 영역 카드 분할:
- 🍚 주식 (밥·면·빵)
- 🥣 국·탕
- 🥗 반찬 3–4가지 (제육볶음, 오이무침, 배추김치…)
- 🍮 후식·음료

각 카드에 해당 메뉴 이름·아이콘·해당 알레르기 배지.

### 3. 영양 정보 (토스 스타일 숫자 카드)
가로 4열 그리드 (모바일 2x2):
- 칼로리 652 kcal · 권장 대비 78%
- 단백질 24 g · 권장 대비 65%
- 탄수화물 85 g · 권장 대비 70%
- 지방 18 g · 권장 대비 60%

숫자는 Pretendard Black 48–64px · 하단에 작은 설명.

### 4. 알레르기 경고 (중요!)
상단 배너 형태 + 필터 칩:
- 오늘 포함된 알레르기 원료 표시 (밝은 노랑 배경 + 경고 아이콘)
- 18개 법정 알레르기 원료 중 해당되는 것만 점등
- "내 알레르기 필터" 토글 → LocalStorage에 학생별 프로필 저장
- 필터 켜면 해당 알레르기 포함 메뉴에 빨간 테두리 + 큰 경고 ⚠️

### 5. 주간 메뉴 달력 (월~금 가로 탭)
- 좌우 스크롤 가로 타임라인
- 각 요일 카드: 날짜 · 대표 메뉴 · 대표 사진 · 별점
- 오늘은 복숭아색 하이라이트
- 클릭 시 해당 날짜 상세로 스크롤/라우팅

### 6. 학생 별점 & 한 줄 감상
- 5점 만점 별 선택 (탭 선호)
- 140자 이내 한 줄 감상 (선택 입력)
- 익명 또는 별명 (학생 실명 금지)
- 최근 6건 실시간 표시 (LocalStorage 또는 Firebase)
- 욕설·광고 필터 안내 (강제 필터는 별도 로직 필요)

### 7. 영양교사 "오늘의 한 끼" 코멘트 (선택 섹션)
- "제철 오이로 만든 무침입니다. 오이에는 비타민C가 풍부해요."
- 아바타 + 영양교사 이름 + 코멘트
- 원산지·지역 먹거리 정보 노출

### 8. 공유 CTA (하단 고정 바)
- "학부모에게 카톡 공유" · "QR 코드 생성" · "내일 메뉴 알림 받기"

## 데이터 구조 (meals.json)

```json
{
  "2026-05-21": {
    "dayOfWeek": "목",
    "photo": "/images/meals/2026-05-21.jpg",
    "photoAlt": "잡곡밥과 제육볶음, 오이무침, 미역국, 배추김치, 요거트",
    "mainDish": "잡곡밥",
    "soup": "미역국",
    "sides": ["제육볶음", "오이무침", "배추김치"],
    "dessert": "요거트",
    "calories": 652,
    "protein": 24,
    "carbs": 85,
    "fat": 18,
    "sodium": 820,
    "dailyRatio": {
      "calories": 78,
      "protein": 65,
      "carbs": 70,
      "fat": 60
    },
    "allergens": ["대두", "돼지고기", "우유"],
    "origin": {
      "쌀": "국내산",
      "돼지고기": "국내산",
      "김치": "국내산 (배추)",
      "오이": "국내산 (강원)"
    },
    "nutritionistNote": "제철 오이로 만든 무침입니다. 오이에는 비타민C가 풍부해요."
  },
  "2026-05-22": { /* ... */ }
}
```

## 알레르기 원료 (교육부 고시 18종)

상수로 선언:

```js
const ALLERGENS = [
  "난류(계란)", "우유", "메밀", "땅콩", "대두", "밀",
  "고등어", "게", "새우", "돼지고기", "복숭아", "토마토",
  "아황산염", "호두", "닭고기", "쇠고기", "오징어", "조개류"
];
```

## 기술 스펙
- **간단 버전**: 단일 HTML + Tailwind CDN + 정적 JSON
- **중간 버전**: Vite + React + LocalStorage 별점
- **고급 버전**: Next.js + Firebase (실시간 별점·댓글)
- 이미지: Unsplash 한식 사진 또는 Imagen 생성 프롬프트 주석

## 콘텐츠 규칙
- ❌ 학생 실명·사진
- ❌ 음식 사진에 학생 등장
- ✅ 음식만 촬영·업로드
- ✅ 별점·감상은 **익명** 또는 별명
- ✅ 알레르기 경고는 **색+텍스트+아이콘 3가지** 병행 (색맹 고려)

## 접근성
- 큰 글씨 모드 (초등 저학년): 18px → 22px 토글
- 알레르기 읽어주기 (TTS 버튼): SpeechSynthesis API
- 색만으로 알레르기 구분 금지 — 🚨 아이콘 + "⚠️ 알레르기 있음" 텍스트
- 터치 타겟 최소 48×48
- WCAG AA 대비 준수

## 산출물
- 단일 `index.html` + `meals.json` (간단 버전)
- 또는 Vite/Next.js 프로젝트 (확장 버전)
- 예시 데이터 2주치 (10일)
- GitHub → Vercel 배포 완료 URL
````

## 🚀 확장 아이디어 · 교육청 NEIS Open API 연동

실제 학교 급식 데이터는 교육청 **NEIS Open API**에서 자동으로 가져올 수 있습니다.

```js
// 예: 한강초 · 2026년 5월
const NEIS_URL = 'https://open.neis.go.kr/hub/mealServiceDietInfo';
const params = {
  KEY: process.env.NEIS_API_KEY,  // 나이스 개발자 포털에서 발급
  Type: 'json',
  ATPT_OFCDC_SC_CODE: 'B10',      // 시도교육청 코드 (서울=B10)
  SD_SCHUL_CODE: '7010123',        // 학교 코드
  MLSV_YMD: '20260521'             // 조회 날짜
};
```

NEIS 응답 → 위 `meals.json` 형식으로 변환 → 매일 자동 업데이트.

**주의**: NEIS API는 **알레르기 원료**를 숫자 코드로 반환합니다. 변환 테이블을 별도 관리해야 해요.

## 🎨 시각 디자인 팁

### 메뉴 카드 시각 차별화
```html
<!-- 주식 (밥) -->
<div class="rounded-3xl p-5 bg-gradient-to-br from-amber-50 to-orange-100 border-2 border-amber-200">
  <span class="text-3xl">🍚</span>
  <h4 class="text-lg font-bold mt-2">잡곡밥</h4>
</div>

<!-- 반찬 -->
<div class="rounded-3xl p-5 bg-gradient-to-br from-green-50 to-emerald-100 border-2 border-green-200">
  <span class="text-3xl">🥗</span>
  <h4 class="text-lg font-bold mt-2">오이무침</h4>
  <span class="inline-block mt-2 px-2 py-0.5 rounded-full bg-red-100 text-red-700 text-xs">
    ⚠️ 대두
  </span>
</div>
```

### 별점 UI (초등 친화)
```html
<div class="flex gap-2">
  <button class="text-4xl" aria-label="별 1점">⭐</button>
  <button class="text-4xl" aria-label="별 2점">⭐</button>
  <button class="text-4xl grayscale opacity-40" aria-label="별 3점">⭐</button>
  <button class="text-4xl grayscale opacity-40" aria-label="별 4점">⭐</button>
  <button class="text-4xl grayscale opacity-40" aria-label="별 5점">⭐</button>
</div>
<p class="text-sm text-center mt-2 text-slate-600">오늘 급식 어땠어요?</p>
```

## 🎯 4회차 실습에 적용하기

이 예제를 4회차 공통 과제로 선택할 경우:

1. **③ AI Studio 명세** 단계에서 위 프롬프트를 기반으로 기능 목록 정리
2. **④ Stitch 화면** 단계에서 위 섹션 1~8을 HTML로 생성
3. **⑥ AI Studio Build 기능 구현** 단계에서:
   - 1차 대화: 라우팅 + `meals.json` 로드
   - 2차 대화: 알레르기 필터 토글 + LocalStorage
   - 3차 대화: 별점 저장 + 주간 집계
4. **⑦⑧ GitHub · Vercel** 배포

## 📝 샘플 프롬프트 (AI Studio Build 1단계)

```text
다음 급식앱 UI를 React + TypeScript + Tailwind 앱으로 만들어주세요.
디자인은 Stitch 원본을 그대로 유지합니다.

## UI
[Stitch HTML 붙여넣기]

## 데이터 (public/meals.json)
[meals.json 10일치 붙여넣기]

## 이번 단계
- meals.json 로드 (useEffect + fetch)
- 오늘 날짜 자동 선택
- 주간 탭에서 다른 날짜 클릭 가능
- 알레르기 · 영양정보는 하드코딩 그대로 노출 (상호작용 다음 단계)

## 제약
- Pretendard + word-break: keep-all
- 18개 법정 알레르기 상수는 constants/allergens.ts 로 분리
- 날짜 포맷: 'YYYY년 M월 D일 (요일)'
```

## ⚠️ 주의 사항

- **개인정보**: 학생 이름·사진·학번·로그인 기능은 **이 앱에서 구현하지 않음**. 별점·감상은 익명/별명만.
- **상업적 표현 금지**: "맛집 리뷰" 같은 상업 서비스 톤 피하고 교육용 어투 유지.
- **알레르기 책임 면책**: 하단 작게 "알레르기 정보는 영양교사 제공 자료에 따릅니다. 개인 알레르기는 의료진 확인 필수" 명시.
- **메뉴 변경 대응**: 급식은 자주 바뀜. 관리자(영양교사)가 쉽게 수정 가능한 구조로.

## 📚 참고 자료

- [교육부 학교 알레르기 유발 식품 18종 고시](https://www.moe.go.kr/)
- [NEIS Open API 포털](https://open.neis.go.kr/)
- 한국영양학회 학령기 권장 섭취량 기준
- [designSkill 03-korean-style](../skills/03-korean-style/SKILL.md) — Iconify Solar 음식 아이콘

## 🔗 관련 예제

- [03-parent-guide](./03-parent-guide.md) — 학부모 안내 앱 (급식앱을 학부모 안내 앱에 통합 가능)
- [10-subject-hub](./10-subject-hub.md) — 교과 자료 허브 (급식앱을 "학교 정보" 허브에 편입 가능)
- [05-attendance](./05-attendance.md) — 출결 대시보드 (교사 전용 페이지 UX 참고)
