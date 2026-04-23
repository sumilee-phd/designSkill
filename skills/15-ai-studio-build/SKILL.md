---
name: ai-studio-build
description: Google AI Studio Build로 Stitch가 만든 UI에 실제 기능(폼 제출·Gemini API·데이터 저장)을 구현해 완결된 앱으로 만드는 방법. 연수 4회차의 핵심 연결 고리.
source: 씨마스에듀 4회차 연수 오리지널
language: ko
priority: ★★★★★
---

# 15. ai-studio-build — AI Studio Build로 기능 구현

> **Stitch는 디자인만 만듭니다. 실제로 동작하게 하는 건 AI Studio Build의 몫입니다.**

## 왜 이 스킬이 필요한가

많은 선생님이 Stitch로 예쁜 UI를 만든 후 이렇게 묻습니다:

> "버튼을 눌렀는데 아무 일도 일어나지 않아요. 이거 어떻게 동작하게 하나요?"

Stitch는 **그림**(HTML·CSS)만 그립니다. 버튼 클릭 시 데이터 저장, 폼 제출, AI 응답 호출 같은 **로직**은 **AI Studio Build**(https://aistudio.google.com/apps)에서 구현합니다.

## 4회차 전체 흐름 속 위치

```
[01~04] AI Studio에서 기능 명세
   ↓
[05~08] Stitch로 UI·디자인 완성
   ↓
[09]    ★ AI Studio Build 로 기능 이식 ← 지금 이 스킬
   ↓
[10]    GitHub push
   ↓
[11]    Vercel 배포
```

## AI Studio Build란

Google이 만든 **자연어 → 앱** 플랫폼.
- URL: https://aistudio.google.com/apps
- 프롬프트로 앱을 생성·수정
- Gemini API 자동 연동 (API 키 없이 시작 가능 — 유료 계정 필요)
- React + TypeScript + Tailwind 자동 스캐폴딩
- 즉시 프리뷰 + GitHub 연동 + Cloud Run 배포 지원
- 자동 저장 · 버전 히스토리

## 📋 Stitch → AI Studio Build 이식 흐름

### ① Stitch에서 HTML·DESIGN.md 준비
```text
stitch-multipage 로 5페이지 완성 →
- index.html (홈)
- about.html
- contact.html
- ...
- DESIGN.md (디자인 토큰)
```

### ② AI Studio Build에서 새 앱 시작
1. https://aistudio.google.com/apps 접속
2. **"Create new app"** 클릭
3. 첫 프롬프트로 **프로젝트 골격** 생성 지시:

```text
다음 Stitch UI에 기능을 구현해 주세요.

[Stitch HTML 붙여넣기 또는 첨부]
[DESIGN.md 붙여넣기]

## 요구 기능
1. "쪽지 보내기" 폼 제출 → 로컬 JSON에 저장 + 성공 토스트
2. "학급 소식" 카드 → LocalStorage에서 최근 5건 로드
3. "담임선생님께 질문하기" → Gemini API로 자동 응답
4. 검색창 → 저장된 소식 중 키워드 매칭

## 기술 제약
- React + TypeScript + Tailwind 유지
- Stitch의 디자인(색·폰트·라운드·그림자) 완전 보존
- Pretendard · word-break: keep-all 유지
- 모든 상호작용에 로딩·성공·실패 상태 포함
```

### ③ 기능별 구현 요청 (대화형)
AI Studio Build는 **대화형**이라 한 번에 모두 요청하기보다 **기능별로 쪼개서** 지시하는 게 효과적입니다.

```text
# 1번 대화
위 UI를 React 프로젝트로 만들어주세요. 아직 기능은 넣지 말고,
모든 화면이 라우팅으로 연결되게만 해주세요.

# 2번 대화
이제 "쪽지 보내기" 폼을 작동하게 해주세요.
- 이름·학번·메시지 필드
- 제출 시 LocalStorage에 저장
- "잘 전달되었어요" 토스트 표시
- 빈 필드는 빨간 테두리로 표시

# 3번 대화
"담임선생님께 질문" 기능을 Gemini API로 구현해주세요.
- 학생이 질문 입력 → Gemini가 5–7학년 눈높이로 답변
- 답변 중에는 로딩 스피너
- 프롬프트는 "당신은 친절한 담임선생님입니다. 학생 눈높이에서 쉽게 설명해주세요."
```

### ④ 빌드·미리보기
- AI Studio Build 우측에 **즉시 프리뷰** 제공
- 수정 후 몇 초 내 반영
- 모바일·태블릿·데스크톱 뷰포트 토글

### ⑤ GitHub 연동
AI Studio Build 우측 상단 **GitHub 아이콘** → Connect
- 자동으로 저장소 생성 (또는 기존 저장소 연결)
- 이후 수정 시 자동 커밋
- 이 GitHub 저장소를 Vercel에 연결 → [14-vercel-deploy](../14-vercel-deploy/SKILL.md)

## 🎯 교사 시나리오별 AI Studio Build 프롬프트

### 시나리오 A. 학급 퀴즈 앱 (examples/02)
```text
Stitch로 만든 퀴즈 UI에 다음 기능을 넣어주세요:
- 문제 5개를 순차적으로 표시
- 각 문제당 30초 타이머
- 답 선택 시 즉시 정답/오답 판정 + 점수 누적
- 5문제 끝나면 결과 화면 (점수 + 틀린 문제 리스트)
- 문제는 `questions.json` 에서 로드
- LocalStorage에 최고 점수 저장
```

### 시나리오 B. 학부모 안내 앱 (examples/03)
```text
Stitch로 만든 학부모 앱 UI에 다음을 구현:
- 공지 3건을 Google Sheets에서 실시간 로드 (Sheets to JSON)
- 설문 폼 → Google Forms 엔드포인트로 POST
- 현장학습 신청 응답 시 확인 이메일 발송 (EmailJS 연동)
- 모든 API 호출 중 로딩·에러 처리 포함
```

### 시나리오 C. 출결 대시보드 (examples/05)
```text
Stitch로 만든 출결 UI에 기능 추가:
- 학생 25명 더미 데이터를 LocalStorage에 저장
- 체크박스 토글로 출결 상태 전환
- 주간·월간 통계 자동 계산
- 엑셀 내보내기 (xlsx 라이브러리)
- 결석 3회 이상 자동 강조
```

### 시나리오 D. 독서록 앱 (examples/07)
```text
Stitch로 만든 독서록 UI를 Gemini와 연동:
- 책 제목 입력 → Gemini가 자동으로 장르·저자·표지 제안
- 감상문 초안 생성 ("당신은 친절한 독서 도우미입니다.")
- 이모지 + 별점 기반 요약 카드 생성
- 월별 독서 통계 자동 생성
```

## ⚠️ AI Studio Build 사용 시 주의사항

### 1. 유료 계정 필요
- 제미나이 유료 계정 (또는 Google One AI Premium)
- 개인 Google 계정으로 준비 — **학교 계정 사용 불가** (연수 공지 참고)

### 2. API 키 보안
- Gemini API를 코드에 직접 넣지 말고 **환경변수**(.env)로 관리
- AI Studio Build → Settings → Environment Variables
- Vercel 배포 시에도 **Environment Variables** 로 다시 등록

### 3. Stitch 디자인 손실 방지
AI Studio Build가 UI를 재해석하면서 Stitch의 디자인을 **조금씩 단순화**하는 경향이 있습니다.

**방지 전략**:
- 첫 프롬프트에 "Stitch의 디자인(색·폰트·그림자·라운드)을 그대로 유지하세요"라고 **명시**
- 결과물 확인 후 변경된 부분이 있으면 "이 부분은 원래 색이 `#FF8A65`였습니다"라고 **수정 지시**
- DESIGN.md 를 첨부하면 토큰 일관성이 높아짐

### 4. 생성된 코드 이해하기
- AI Studio Build가 만드는 코드는 **실제로 동작**하지만 최적화는 별도
- 배포 전 한 번 읽어보고, 이상한 부분은 Claude Code나 Cursor로 다듬기
- 특히 **접근성**(aria-label, 키보드 탐색)은 별도 요청해야 잘 들어감

### 5. 민감 정보 취급
- 학생 실명·학번·전화번호는 **더미 데이터**만 사용
- 실제 배포 시에는 학교 공식 시스템(EduFine, 나이스)과 연결 고려
- Vercel Free 플랜은 공개 URL이므로, 민감 정보는 환경변수·백엔드 분리 필수

## 🔗 AI Studio Build ↔ 다른 스킬 연결

| 앞 단계 | AI Studio Build | 뒷 단계 |
|---|---|---|
| [03-stitch-multipage](../11-stitch-multipage/SKILL.md) 완료 | **→ 기능 이식 →** | [09-react-convert](../09-react-convert/SKILL.md) 로 구조 정돈 |
| [DESIGN.md](../01-design-md/SKILL.md) 첨부 | **→ 토큰 유지 →** | [10-shadcn-ui](../10-shadcn-ui/SKILL.md) 로 컴포넌트 표준화 |
| 단일 HTML 5개 | **→ React 앱 통합 →** | [14-vercel-deploy](../14-vercel-deploy/SKILL.md) |

## 💡 Pro Tip — 프롬프트 템플릿

AI Studio Build에 바로 붙여 넣을 수 있는 한국어 템플릿:

```text
# 프로젝트: [프로젝트명]

## 기존 자산
- UI HTML: [Stitch 결과물 붙여넣기]
- DESIGN.md: [디자인 시스템 붙여넣기]

## 목표
이 UI를 React + TypeScript + Tailwind 앱으로 변환하되,
디자인(색·폰트·그림자·라운드)은 **그대로 유지**해주세요.

## 구현할 기능 (우선순위 순)
1. [기능 1]
2. [기능 2]
3. [기능 3]

## 기술 제약
- Pretendard Variable + word-break: keep-all
- 모든 상호작용에 로딩·성공·실패 상태
- 접근성: WCAG AA 대비, 모든 interactive 요소에 aria-label
- 민감 정보는 더미 데이터

## 폼 처리
- 제출 실패 시 한국어 에러 메시지
- 성공 시 토스트 + LocalStorage 저장
- 빈 필드는 빨간 테두리 + 안내

## 배포 준비
- Vercel 배포를 전제로 구조화
- 환경변수로 API 키 관리
- `npm run build` 가 에러 없이 통과
```

## 📚 참고 자료

- [AI Studio Build 공식](https://aistudio.google.com/apps)
- [Gemini API 문서](https://ai.google.dev/)
- [Stitch → AI Studio Build 가이드 (Google)](https://ai.google.dev/build)
- 연수 강사 메모: 1차 시도에서 디자인이 바뀌면 **프롬프트를 더 구체적으로**. 한 번에 다 만들려 하지 말고 **기능 1개씩** 쪼개서 진행.
