# 🛠️ 4회차 도구별 기능 카탈로그 · 급식앱 시연 가이드

> **용도**: 연수 4회차 시연에서 "이 기능은 어느 도구에서 구현하지?"를 바로 찾아보는 레퍼런스
> **예시 프로젝트**: 급식앱 (examples/11-meal-app · meal-bistro 프리셋)
> **업데이트**: 2026.05

---

## 📊 전체 워크플로 한눈에 — 책임 매트릭스

급식앱의 **기능별로 어느 도구에서 뭘 하는지** 한 장으로 정리:

| 기능 | 🎨 Stitch | ⚙️ AI Studio Build | 📦 GitHub | 🚀 Vercel |
|---|---|---|---|---|
| **Hero 디자인** (CHEF'S PICK · 사진) | ✅ 화면 생성 | — | — | — |
| **4카테고리 그리드** (STAPLE/SOUP/SIDE/TRAD) | ✅ 레이아웃 | — | — | — |
| **요일 탭 UI** (MON–FRI) | ✅ 외형 | ✅ 클릭 상태 관리 | — | — |
| **하단 탭 내비게이션** | ✅ 외형 | ✅ 라우팅 | — | — |
| **meals.json 로딩** | — | ✅ fetch + useEffect | ✅ 저장 | ✅ public/ 호스팅 |
| **별점 저장** | ✅ 별 UI | ✅ LocalStorage 로직 | — | — |
| **18 알레르기 필터** | ✅ 그리드 | ✅ state + 필터링 | — | — |
| **TTS 읽어주기** | — | ✅ SpeechSynthesis API | — | — |
| **Gemini API로 영양 해설** | — | ✅ API 호출 | — | ✅ 환경변수 |
| **NEIS 급식 자동 로드** | — | ✅ fetch 구현 | ✅ API 키 secret | ✅ Serverless (CORS 우회) |
| **카카오톡 공유** | ✅ 버튼 UI | ✅ 카카오 SDK | — | — |
| **QR 코드 생성** | ✅ 자리만 | ✅ qrcode.js 통합 | — | — |
| **다크 모드** | ✅ 토큰 정의 | ✅ 토글 로직 | — | — |
| **학기별 버전 관리** | — | — | ✅ 브랜치/태그 | ✅ Preview |
| **영양교사 협업** | — | — | ✅ Collaborators | — |
| **사용자 방문 통계** | — | — | — | ✅ Analytics |
| **모바일 속도 측정** | — | — | — | ✅ Speed Insights |
| **커스텀 도메인** (meals.myschool) | — | — | — | ✅ Domains |
| **코드 저장 · 공유** | — | — | ✅ Push | — |
| **자동 배포** | — | ✅ GitHub 연동 | ✅ push 감지 | ✅ 빌드·배포 |

---

## 🎨 1. Stitch에서 가능한 기능

> **역할**: **"그림"을 만드는 단계**. UI 디자인·레이아웃·색·타이포를 자연어 프롬프트로 생성.
> **URL**: https://stitch.withgoogle.com/
> **입력**: 프롬프트 + (선택) 기존 이미지 업로드
> **출력**: HTML + CSS (Tailwind) / React 코드 / Figma export

### ✅ 할 수 있는 일

| 카테고리 | 기능 | 급식앱 적용 예시 |
|---|---|---|
| **화면 생성** | 단일 페이지 HTML | 홈·메뉴·후기·프로필 각 1장씩 |
| | 멀티 페이지 사이트 | 4개 화면 한 번에 생성 (stitch-multipage 스킬) |
| | 컴포넌트 라이브러리 | Button · Card · Nav 등 재사용 단위 |
| **디자인 시스템** | 색 팔레트 적용 | meal-bistro의 크림+올리브 토큰 |
| | 타이포그래피 | Pretendard + uppercase 영문 레이블 |
| | 간격·라운드 일관화 | Hero 24 / 카드 16 / 배지 4 |
| **레이아웃** | 반응형 (모바일 → 데스크톱) | 430px 폭 기준 + 태블릿 2컬럼 |
| | 그리드·플렉스 조합 | 4카테고리 2×2 그리드 |
| | Safe Area 대응 주석 | 하단 탭 padding: env(safe-area-inset-bottom) |
| **비주얼** | Hero 사진 영역 | 4:5 비율 · 하단 그라디언트 오버레이 |
| | 아이콘 선택 (Iconify) | solar:fork-knife, solar:chef-hat |
| | 배지·태그 디자인 | CHEF'S PICK 올리브 라벨 |
| **상호작용 서술** | Hover · Focus · Active 스타일 | 카드 hover 시 2px 상승 |
| | 애니메이션 키프레임 | 별점 클릭 시 0.2s bounce |
| **접근성** | alt 텍스트 명시 | 모든 음식 사진 alt 한국어 서술 |
| | 색 대비 고려 | 크림 #F5E9C8 + 잉크 #2C2818 (AA 이상) |
| | 큰 글씨 모드 toggle UI | 프로필 탭 접근성 섹션 |

### ❌ Stitch에서 안 되는 것

- 실제 데이터 연동 (단순 placeholder만)
- 폼 제출·LocalStorage 저장
- API 호출 (Gemini, NEIS 등)
- 인증·로그인
- 동적 state 관리

### 💬 Stitch 실전 프롬프트 (급식앱 홈 화면)

````text
@SKILL.md
@presets/education/meal-bistro.md
DIALS: VARIANCE=5, MOTION=3, DENSITY=5

# 씨마스고등학교 급식앱 · 홈 화면 (모바일)

## 레이아웃 (430px 세로)
1. 상단 헤더 (64px)
   - 로고 🏫 + "씨마스고등학교"
   - 우측: 🔔 알림 · 🔍 검색 아이콘

2. Hero 카드 (4:5 비율 · 라운드 24px)
   - 배경: 오늘 메인 메뉴 사진 (치즈돈까스)
   - 상단 좌측 배지: "CHEF'S PICK" (올리브 그린 #5A6B3E 배경 + 흰 텍스트)
   - 하단 그라디언트 오버레이 (검정 85%→투명)
   - 오버레이 위 텍스트 (흰색):
     - 작은 kicker: "SPECIAL MENU" (uppercase 0.14em)
     - 큰 제목: "2026년 5월 21일 (목) 오늘의 메뉴"
     - 서브: "🍽️ 치즈돈까스 정식"

3. 2카드 퀵 액션 (가로 그리드, 간격 12px)
   - 카드 A: 📅 주간 식단 + "한 주간의 즐거운 소식"
   - 카드 B: 💬 문의·피드백 + "더 맛있는 식탁을 위해"
   - 각 카드: 크림 #FAF3DC 배경, 라운드 16px, 패딩 20px

4. 하단 탭 내비 (고정 64px)
   - 🏠 홈 (active: 올리브 원형 배경)
   - 🍽️ 메뉴
   - ⭐ 후기
   - 👤 프로필

## 제약
- Pretendard · word-break: keep-all
- 전체 배경 #F5E9C8 크림
- Safe Area 상·하 반영
- 다크 모드 토큰도 같이 만들어줘
````

### 🔧 Stitch 안에서 미세 조정

Stitch 에디터 자체에서도:
- 색 토큰 개별 수정 (색상 팔레트 UI)
- 폰트 크기 슬라이더
- 컴포넌트 variant 생성 (예: Button default/hover/disabled)
- 화면 복제 → 수정 (같은 디자인의 다른 상태)
- Figma로 export → Figma에서 더 정밀 편집

---

## ⚙️ 2. AI Studio Build에서 미세조정 가능한 기능

> **역할**: **"그림에 생명을 불어넣는 단계"**. Stitch HTML을 React 앱으로 이식하고, 상태·API·저장 등 실제 동작 구현.
> **URL**: https://aistudio.google.com/apps
> **입력**: 대화형 프롬프트 (기능별로 쪼개서)
> **출력**: 완전한 React + TypeScript + Tailwind 프로젝트 + GitHub 자동 연동

### ✅ 대화로 구현/조정 가능한 기능

#### A. 구조·라우팅
- react-router-dom 기반 멀티 페이지 라우팅
- 하단 탭 네비 상태 연동
- 뒤로가기·이력 관리
- Dynamic routes (`/menu/:date`)
- 404 페이지

**조정 프롬프트 예시**:
```
하단 탭 네비를 추가해주세요.
- 4탭: 홈(/), 메뉴(/menu), 후기(/review), 프로필(/profile)
- 현재 라우트에 따라 액티브 탭이 올리브 원형 배경으로 강조
- Safe Area 하단 패딩 env(safe-area-inset-bottom) 적용
- 탭 전환 시 페이지 전환 애니메이션 fade 0.2s
```

#### B. 상태 관리
- `useState` 기본 / Zustand 전역 / Context API
- 폼 상태 (react-hook-form 또는 controlled)
- 복잡한 필터·검색 상태
- URL 쿼리 스트링 동기화

**조정 프롬프트 예시**:
```
요일 탭(MON~FRI)을 상태로 관리하고,
선택된 요일에 따라 meals.json에서 해당 날짜 메뉴만 렌더하세요.
- 기본값: 오늘 날짜
- 오늘이 주말이면 가장 가까운 금요일로
- 선택한 요일은 URL 쿼리에 ?day=2026-05-21 로 반영
```

#### C. 데이터 & 스토리지
- `fetch`로 JSON 로드
- `localStorage` 저장·복원
- `sessionStorage`
- `IndexedDB` (대용량)
- Firebase Firestore (실시간 DB)
- Supabase (Postgres)

**조정 프롬프트 예시**:
```
별점·감상을 LocalStorage에 저장하세요.
- 키: "meals-reviews"
- 값: { "2026-05-21": [{ nickname, rating, comment, timestamp }] }
- 최근 50건만 보관 (오래된 순 삭제)
- 후기 탭 로드 시 최근 10건을 시간 역순으로 렌더
```

#### D. 외부 API 연동
- Google Gemini API (`@google/generative-ai`)
- NEIS Open API (급식 데이터)
- Kakao SDK (공유)
- Web Speech API (TTS/STT)
- 카카오 지도·네이버 지도

**조정 프롬프트 예시**:
```
메뉴 상세에서 "🔊 읽어주기" 버튼 누르면 Web Speech API로 메뉴를 읽어주세요.
- 읽을 내용: "오늘은 치즈돈까스 정식입니다. 백미밥, 어니언스프..."
- 한국어 음성 (ko-KR)
- 읽는 중에는 버튼이 "⏸️ 중지" 로 변경
- 알레르기 포함 메뉴는 강조해서 읽어주기 ("주의! 우유 알레르기 있어요")
```

#### E. Gemini AI 통합
- 텍스트 생성 (영양 설명·추천 메시지)
- 이미지 분석 (급식 사진 → 자동 태그)
- 다중 턴 대화
- 스트리밍 응답
- System prompt 커스터마이징

**조정 프롬프트 예시**:
```
영양교사 탭에 "오늘의 해설 자동 생성" 기능 추가.
- 버튼 누르면 오늘 메뉴(치즈돈까스, 백미밥, ...)를 Gemini에게 전달
- 시스템 프롬프트: "당신은 친절한 영양교사입니다. 중학생 눈높이로
  오늘 메뉴의 영양·제철·조리법을 3문장으로 설명해주세요."
- 응답을 타이핑 애니메이션으로 렌더
- 만족스러운 결과는 "저장" → meals.json의 nutritionistNote 업데이트
- API 키는 환경변수 VITE_GEMINI_API_KEY 사용
```

#### F. 사용자 경험
- 로딩 스피너·스켈레톤
- 토스트 알림
- 모달·드로어
- 스와이프 제스처 (좌우)
- 무한 스크롤 / 페이지네이션
- 검색·필터링

**조정 프롬프트 예시**:
```
모든 async 작업에 로딩 UX 추가:
- meals.json 로딩 중: 스켈레톤 카드 (Hero + 4그리드)
- Gemini API 호출 중: 하단 토스트 "해설을 작성하고 있어요..."
- 저장 성공: 토스트 "✓ 저장되었어요" 2초
- 실패: 빨간 토스트 + 재시도 버튼
```

#### G. 접근성 (A11y)
- ARIA 속성 추가
- 키보드 내비게이션
- 포커스 관리
- prefers-reduced-motion 대응
- prefers-color-scheme 대응

**조정 프롬프트 예시**:
```
모든 interactive 요소에 aria-label을 한국어로 추가.
예:
- 별점 버튼: aria-label="별 3점 주기"
- 알레르기 체크: aria-label="난류 알레르기 선택 (현재 미선택)"
- 탭 버튼: aria-label="홈 탭으로 이동"
키보드 Tab 순서가 논리적으로 흐르도록 정리.
```

#### H. 스타일 미세조정
- 특정 컴포넌트 색 수정
- 간격·폰트 크기 조정
- 특정 상태 스타일 추가
- 다크 모드 토큰 보강

**조정 프롬프트 예시**:
```
ChefPickBadge 컴포넌트를 조정:
- 현재는 #5A6B3E 고정
- "평균 별점 4.5점 이상인 메뉴"에만 자동 표시하도록 prop 기반으로 변경
- 4.5 이상: CHEF'S PICK (올리브)
- 4.0~4.5: POPULAR (앰버 #D4923A)
- 그 외: 배지 없음
```

#### I. 성능 최적화
- 이미지 lazy loading
- 코드 스플리팅
- React.memo
- useMemo / useCallback
- 번들 크기 분석

**조정 프롬프트 예시**:
```
성능 개선:
- 메뉴 사진 모두 loading="lazy" + <img srcset> 반응형
- 요일 탭 클릭 시 해당 날짜 사진만 prefetch
- React.memo로 CategoryCard 불필요 리렌더 방지
- 프로필 탭은 React.lazy로 코드 스플리팅
```

#### J. 에러 핸들링·디버깅
- try/catch 전역 감싸기
- Error Boundary 컴포넌트
- 콘솔 에러 해결
- TypeScript 타입 오류 수정

**조정 프롬프트 예시**:
```
콘솔에 이런 에러가 나와요: [에러 메시지 붙여넣기]
원인 파악하고 수정해주세요.
근본 원인도 설명해주세요 (같은 에러 재발 방지).
```

### ❌ AI Studio Build에서 안 되는 것
- 디자인 시스템의 전면 개편 (이건 Stitch에서)
- 완전히 다른 프레임워크 전환 (Vue, Svelte 등)
- 백엔드 서버 구축 (Express, FastAPI 등 — Serverless function으로는 가능)

---

## 📦 3. GitHub에서 적용 가능한 부분

> **역할**: **"코드의 구글 드라이브 + 협업 허브"**. 버전 관리·백업·협업·자동화.
> **URL**: https://github.com/sumilee-phd/meals
> **입력**: 코드 커밋 / 이슈 / PR
> **출력**: 히스토리·릴리스·배포 트리거

### ✅ meals 앱에 바로 쓰는 기능

#### A. 기본 버전 관리
- 커밋 히스토리로 학기별 변경 추적
- 브랜치로 새 학기 준비 (`feature/2026-2-semester`)
- 태그로 학기별 릴리스 고정 (`v2026.1`)
- `git revert` 로 실수 되돌리기

#### B. 협업 기능

**Collaborators 추가** (영양교사·담임 공동 관리):
```
Settings → Collaborators → Add people
→ 영양선생님 GitHub ID 초대
→ "Write" 권한 부여
```

**Issue 템플릿** (학생·학부모 피드백 수집):
```markdown
# .github/ISSUE_TEMPLATE/meal-feedback.md
---
name: 급식 피드백
about: 급식 맛·양·메뉴에 대한 의견
title: '[FEEDBACK] '
labels: 'feedback'
---
## 날짜
2026-05-__

## 메뉴
어떤 메뉴에 대한 의견인가요?

## 내용
(구체적으로 작성)
```

**Pull Request** (변경사항 코드 리뷰):
- 새 학기 메뉴 업데이트는 PR로
- 동료 교사가 리뷰 후 머지

#### C. 자동화 (GitHub Actions)

**매일 아침 NEIS에서 급식 자동 업데이트**:
```yaml
# .github/workflows/daily-meal-sync.yml
name: Daily meal sync from NEIS
on:
  schedule:
    - cron: '0 22 * * *'  # UTC 22:00 = KST 07:00
  workflow_dispatch:  # 수동 실행도 가능
jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Fetch NEIS API
        run: |
          curl "https://open.neis.go.kr/hub/mealServiceDietInfo?KEY=${{ secrets.NEIS_API_KEY }}&Type=json&ATPT_OFCDC_SC_CODE=B10&SD_SCHUL_CODE=7010123&MLSV_YMD=$(date +%Y%m%d -d tomorrow)" \
            > public/meals-raw.json
      - name: Transform to meals.json
        run: node scripts/neis-transform.js
      - name: Commit if changed
        run: |
          git config user.email "bot@school.go.kr"
          git config user.name "Meal Bot"
          git add public/meals.json
          git diff --cached --quiet || git commit -m "chore: daily meal sync"
          git push
```

#### D. Secrets 관리

**Settings → Secrets and variables → Actions**:
```
NEIS_API_KEY=abc123...
GEMINI_API_KEY=AIza...
KAKAO_APP_KEY=xyz789...
```
→ 코드에 절대 하드코딩 금지, Actions에서만 접근.

#### E. README · 문서화

**README.md 예시**:
```markdown
# 씨마스고등학교 급식앱 🍱

[![Deploy](https://deploy-badge.vercel.app/vercel/meals)]()

## 링크
- 🚀 라이브: https://meals.vercel.app
- 📋 이슈·피드백: [Issues](./issues)

## 로컬 실행
\`\`\`bash
npm install
npm run dev
\`\`\`

## 데이터 관리
영양교사는 `public/meals.json`에 메뉴 입력
(또는 GitHub Actions가 NEIS에서 자동 업데이트)

## 라이선스
MIT
```

#### F. Template Repository

**Settings → General → Template repository 체크**
→ 다른 학교 선생님이 "Use this template" 한 번으로 복제 가능.

#### G. GitHub Pages (Vercel 대안)

정적 사이트면 무료로 `{username}.github.io/meals` 주소 제공:
```
Settings → Pages → Source: main / (root) or /docs
```

### 🔒 Security 체크

- [ ] `.env` 파일은 `.gitignore`에 포함
- [ ] API 키 커밋 로그에 없는지 확인 (`git log --all -p | grep "AIza"`)
- [ ] Dependabot 자동 의존성 업데이트 활성화
- [ ] Branch protection rules (main에 직접 push 금지)

---

## 🚀 4. Vercel에서 적용할 부분

> **역할**: **"인터넷에 URL을 만들어주는 배포 플랫폼"**. HTTPS·CDN·자동 배포·모니터링.
> **URL**: https://vercel.com/dashboard
> **입력**: GitHub 저장소
> **출력**: 라이브 URL + 성능 지표 + 분석

### ✅ meals 앱에 활용 가능한 기능

#### A. 기본 배포
- GitHub 저장소 연결
- `main` 브랜치 push → 자동 프로덕션 배포
- 다른 브랜치·PR → Preview 배포 (URL 별도)
- 배포 로그 + 빌드 시간 기록
- 배포 실패 시 자동 롤백

#### B. 환경 변수 관리

**Settings → Environment Variables**:
| 변수 | 값 | 환경 |
|---|---|---|
| `VITE_GEMINI_API_KEY` | `AIza...` | Production · Preview |
| `VITE_NEIS_API_KEY` | `abc123...` | Production |
| `VITE_KAKAO_APP_KEY` | `xyz789...` | Production |
| `VITE_SCHOOL_CODE` | `7010123` | Production · Preview |

→ 코드에서 `import.meta.env.VITE_GEMINI_API_KEY` 로 접근.

#### C. 커스텀 도메인

**Settings → Domains**:
```
meals-sumilee-phd.vercel.app  ← 기본
meals.myschool.go.kr          ← 학교 공식 도메인 (선택)
```

DNS 설정 (학교 도메인 관리자에게 요청):
```
Type: CNAME
Host: meals
Value: cname.vercel-dns.com
```

SSL 인증서는 Vercel이 자동 발급.

#### D. Analytics (무료 Hobby 플랜 포함)

**Analytics 탭**:
- 방문자 수 (시간별·일별)
- 페이지별 인기도 (`/menu` vs `/review`)
- 유입 경로 (검색·직접·SNS)
- 국가·디바이스별

→ 영양교사에게 "이번 주 급식 페이지 조회 1,243회" 리포트 가능.

#### E. Speed Insights

**Speed Insights 탭**:
- Core Web Vitals (LCP, FID, CLS)
- 실제 사용자의 모바일 로딩 속도
- 페이지별 성능 점수

→ 급식 사진이 커서 느려지면 자동 경고.

#### F. Serverless Functions

**api/ 폴더에 함수 파일**:
```ts
// api/neis-proxy.ts (CORS 우회)
import type { VercelRequest, VercelResponse } from '@vercel/node';

export default async function handler(req: VercelRequest, res: VercelResponse) {
  const { date } = req.query;
  const url = `https://open.neis.go.kr/hub/mealServiceDietInfo?KEY=${process.env.NEIS_API_KEY}&Type=json&ATPT_OFCDC_SC_CODE=B10&SD_SCHUL_CODE=${process.env.SCHOOL_CODE}&MLSV_YMD=${date}`;
  const response = await fetch(url);
  const data = await response.json();
  res.status(200).json(data);
}
```
→ `/api/neis-proxy?date=20260521` 로 호출 가능.

#### G. Edge Functions

더 빠른 응답 필요 시 (Geo 기반 CDN):
```ts
// api/chef-pick.ts
export const config = { runtime: 'edge' };

export default async function handler() {
  return new Response(JSON.stringify({ pick: "치즈돈까스 정식" }), {
    headers: { 'content-type': 'application/json' }
  });
}
```

#### H. Cron Jobs (Pro 플랜)

**vercel.json**:
```json
{
  "crons": [
    {
      "path": "/api/daily-sync",
      "schedule": "0 22 * * *"
    }
  ]
}
```
→ 매일 아침 7시(UTC 22시)에 NEIS에서 자동 동기화.

*Hobby 플랜에서는 GitHub Actions로 대체 (위 섹션 3-C 참조)*

#### I. Image Optimization

`next/image` 또는 Vercel Image Optimization:
```tsx
<img
  src="/_next/image?url=/images/meals/2026-05-21.jpg&w=640&q=75"
  alt="치즈돈까스"
  loading="lazy"
/>
```
- 자동 WebP 변환 (-70% 용량)
- 디바이스별 해상도 대응
- CDN 캐싱

#### J. Rewrites · Redirects

**vercel.json**:
```json
{
  "rewrites": [
    { "source": "/today", "destination": "/menu?day=today" }
  ],
  "redirects": [
    { "source": "/old-menu", "destination": "/menu", "permanent": true }
  ]
}
```
→ `meals.vercel.app/today` 같은 예쁜 URL 제공.

#### K. Headers (보안)

**vercel.json**:
```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "X-Content-Type-Options", "value": "nosniff" },
        { "key": "X-Frame-Options", "value": "DENY" },
        { "key": "Referrer-Policy", "value": "strict-origin-when-cross-origin" },
        { "key": "Content-Security-Policy", "value": "default-src 'self'; img-src * data:; style-src 'self' 'unsafe-inline'" }
      ]
    }
  ]
}
```

#### L. 배포 보호 (개발 중)

**Settings → Deployment Protection**:
- Password Protection: 비밀번호 걸기 (학부모 공개 전 테스트)
- Trusted IPs: 특정 IP만 접근 허용

#### M. Spend Management

**Settings → Spend Management** (트라이얼 전에 꼭!):
```
월 한도: $20 (Hobby 무료 한도)
알림: 50%, 80%, 100%
100% 도달 시 자동 일시 중지
```

#### N. Webhooks · Notifications

- Slack·Discord·Email에 배포 알림
- "main에 push → Slack 채널에 자동 메시지"

### 🔧 Vercel 대시보드 체크포인트

연수 시연에서 학생과 함께 확인할 것:
- [ ] Deployments 탭 — 커밋마다 URL 생성되는지
- [ ] Analytics — 실시간 방문자 (휴대폰으로 접속해 보기)
- [ ] Speed Insights — 모바일 성능 점수
- [ ] Logs — 실시간 서버 로그

---

## 🍱 전체 흐름 매핑 (급식앱 실전)

### 시나리오: 영양교사가 새 학기 첫 급식을 등록·공유하기까지

```
┌─────────────────────────────────────────────────────────────────┐
│ 📅 월요일 오전 7시                                              │
│                                                                 │
│ 영양교사가 이번 주 메뉴를 Google Sheets에 입력                  │
│         ↓                                                       │
│ GitHub Actions cron (자동 실행)                                 │
│ → Sheets/NEIS에서 데이터 fetch                                  │
│ → meals.json 으로 변환                                          │
│ → main 브랜치에 자동 커밋                                       │
│         ↓                                                       │
│ Vercel webhook 감지                                             │
│ → 빌드 (1~2분)                                                  │
│ → 프로덕션 URL 갱신                                             │
│         ↓                                                       │
│ 학생이 오전 8시 휴대폰으로 meals.myschool.go.kr 접속            │
│ → Vercel CDN에서 즉시 응답 (edge 캐싱)                          │
│ → 오늘 메뉴 "치즈돈까스 정식" 즉시 로드                         │
│         ↓                                                       │
│ 학생이 별점 ⭐⭐⭐⭐⭐ 입력                                   │
│ → LocalStorage 저장 (브라우저에만)                              │
│ → 후기 탭에 익명 별명으로 노출                                  │
│         ↓                                                       │
│ 교사가 Analytics 확인                                           │
│ → "오늘 조회 342회, 별점 평균 4.6"                              │
└─────────────────────────────────────────────────────────────────┘
```

### 도구별 "누가 무엇을 하는가" 체크리스트

| 주체 | 도구 | 무엇을 하나 | 빈도 |
|---|---|---|---|
| **강사(이수미)** | Stitch | 초기 4개 화면 디자인 생성 | 1회 |
| | AI Studio Build | 기능 이식 · 앱 완성 | 1회 |
| | GitHub | 초기 저장소 생성 · README 작성 | 1회 |
| | Vercel | 최초 배포 연결 · 환경변수 등록 | 1회 |
| **영양교사** | Google Sheets | 매주 메뉴 입력 | 매주 |
| | GitHub (선택) | 직접 meals.json 편집 · PR | 필요 시 |
| **학생·학부모** | 브라우저 | URL 접속 · 별점·감상 | 매일 |
| **자동화 (봇)** | GitHub Actions | 매일 NEIS 동기화 | 매일 |
| | Vercel | 자동 빌드·배포 | 커밋마다 |

---

## 💡 연수 시연 순서 제안 (150분 내)

```
[0:00–0:10] 이 레퍼런스 문서 소개 · 급식앱 예시 선정 이유
[0:10–0:35] Stitch 실전 ─ 4화면 디자인 생성 (위 프롬프트 실행)
[0:35–1:00] AI Studio Build ─ 기능 A→B→C 순차 이식
[1:00–1:15] GitHub ─ 저장소 생성 · Secrets · (선택) Actions 맛보기
[1:15–1:30] Vercel ─ Import · Deploy · Analytics 확인
[1:30–1:45] 기능 조정 라이브 Q&A (학생이 원하는 기능 즉석 구현)
[1:45–2:30] 학생 실습 + 배포 + 공유
```

---

## 📚 관련 자료

- [designSkill 메인](../README.md)
- [급식앱 예제 (11-meal-app.md)](../examples/11-meal-app.md)
- [meal-bistro 프리셋](../presets/education/meal-bistro.md)
- [ai-studio-build 스킬](../skills/15-ai-studio-build/SKILL.md)
- [vercel-deploy 스킬](../skills/14-vercel-deploy/SKILL.md)
- [stitch-multipage 스킬](../skills/11-stitch-multipage/SKILL.md)

---

**© 2026 이수미 · 씨마스에듀 · MIT License**
