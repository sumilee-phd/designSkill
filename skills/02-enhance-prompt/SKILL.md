---
name: enhance-prompt
description: 모호한 UI 아이디어를 Stitch·Claude·Gemini에 바로 넣을 수 있는 고품질 프롬프트로 변환. UI/UX 키워드 주입, 디자인 시스템 컨텍스트 첨부, 구조화된 섹션 제공.
source: google-labs-code/stitch-skills
language: ko
---

# 02. enhance-prompt — 프롬프트 강화기

## 언제 사용하나

- "학급 홍보 페이지 만들어줘" 같은 **한 줄짜리 요청**을 받았을 때
- Stitch·Gemini에 넣을 프롬프트가 **너무 짧아 결과가 밋밋**할 때
- DESIGN.md 와 맥락이 **자동으로 결합된 프롬프트**가 필요할 때

## 변환 규칙 — 5단계

### ① 사용자 의도 파악
원본 프롬프트에서 3가지를 추출합니다.
- **무엇을**(WHAT): 페이지 종류 · 주요 기능
- **누가**(WHO): 타깃 유저 (교사/학생/학부모)
- **왜**(WHY): 성공 기준 (전환·정보 전달·재미)

### ② 구조 골격 첨부
```
[페이지 레이아웃]
- Hero: [한 줄 요약 + CTA]
- Features: 3–6개 섹션
- Social Proof / 후기
- FAQ
- Footer CTA

[컴포넌트 목록]
- Navigation · Button · Card · Form · Modal · Empty State · Loading
```

### ③ 비주얼 디렉션 주입
- **반드시** DESIGN.md (없다면 `presets/education/classroom-pastel.md`)를 참조하게 한다
- **반드시** Pretendard · 한국어 줄바꿈 규칙 포함
- 5개 이상의 **구체 스타일 키워드**를 붙인다 (예: "라운드 16px, 글래스모피즘, 부드러운 그림자")

### ④ 콘텐츠 예시 제공
플레이스홀더 대신 **진짜 한국어 예문** 제공:
```text
Hero 타이틀: "4학년 3반, 우리들의 이야기를 만나보세요"
Hero 서브: "한 학기 동안의 프로젝트·봉사·발표를 한 페이지에 담았어요"
Primary CTA: "학급 소식 보러가기"
Secondary CTA: "담임선생님께 쪽지 남기기"
```

### ⑤ 제약·금지 항목 명시
- ❌ Lorem Ipsum 금지
- ❌ 영어 플레이스홀더 금지
- ❌ 빈 섹션·TODO 주석 금지
- ✅ 모든 이미지는 Unsplash URL 또는 Imagen 프롬프트 주석으로

## 변환 예시

### Before (사용자 원본)
```
"우리 반 페이지 만들어줘"
```

### After (강화된 프롬프트)
```
# 프로젝트: 4학년 3반 학급 페이지

## 목표
담임·학부모·학생이 한 학기 활동을 한눈에 보는 공식 학급 홍보 페이지.
모바일에서도 부드럽게 읽히고, 학부모가 3분 안에 전체 내용을 훑을 수 있게.

## 참조 디자인
@presets/education/classroom-pastel.md 를 기준으로.
Pretendard Variable · word-break: keep-all · 라운드 16px · Level 1 그림자.

## 구조
1. Hero (70vh)
   - 타이틀: "4학년 3반, 우리들의 이야기를 만나보세요"
   - 서브: "한 학기 동안의 프로젝트·봉사·발표를 한 페이지에 담았어요"
   - Primary CTA: "학급 소식 보러가기"
   - 배경: 파스텔 복숭아 그라디언트 + 손그림 일러스트
2. 반 소개 섹션 (아바타 + 담임 인사말 400자)
3. 이번 학기 프로젝트 3개 카드 (이미지 + 제목 + 150자)
4. 학생 한 줄 소감 캐러셀 (6–8개)
5. 학부모 안내 FAQ (접히는 아코디언 5개)
6. 담임 연락 섹션 (쪽지 폼 + 이메일 링크)

## 컴포넌트
- Navigation: 스크롤 시 배경 반투명
- Card: 라운드 16px, hover시 Level 2 그림자로 상승
- Button Primary: 복숭아 → 산호 그라디언트
- FAQ: 펼칠 때 smooth 0.3s

## 제약
- 학생 개인정보(이름·전화·주소)는 모두 익명 처리 (예: "지수 ★", "도윤 ▲")
- 이미지는 모두 Unsplash source 또는 Imagen 프롬프트 주석
- 모바일 첫 스크롤 안에 Hero + Primary CTA 보이도록
- 접근성: 색 대비 AA 이상, 포커스 링 선명하게

## 출력
단일 `index.html` · Tailwind CDN · Pretendard CDN · Iconify Solar 아이콘
```

## 사용 방법

```text
사용자: @skills/02-enhance-prompt 로 다음 프롬프트 강화해줘: "퀴즈 앱 만들어줘"
AI: [5단계 적용 → 구조화된 완전 프롬프트 출력]
```

## 참고

원본: [google-labs-code/stitch-skills/enhance-prompt](https://github.com/google-labs-code/stitch-skills/tree/main/skills/enhance-prompt)
