# 예제 01 — 학급 홍보 페이지

> **시나리오**: 4학년 3반 담임이 학기 말 학부모·학생·동료 교사에게 보여줄 학급 소개 페이지를 만든다.
> **소요 시간**: Stitch + Vercel 30–40분
> **난이도**: ⭐ 입문

## 프롬프트

````text
@SKILL.md
@presets/education/classroom-pastel.md 참조.
DIALS: VARIANCE=5, MOTION=4, DENSITY=4

# 프로젝트: 한강초 4학년 3반 홍보 페이지

## 목적
- 학부모와 동료 교사가 우리 반의 한 학기를 한눈에 볼 수 있는 공식 페이지
- 모바일에서도 편안히 읽히고, 학부모가 3분 안에 전체를 훑을 수 있게

## 페이지 구조 (단일 index.html)
1. Hero (70vh)
   - 타이틀: "4학년 3반, 우리들의 이야기를 만나보세요"
   - 서브: "한 학기 동안의 프로젝트·봉사·발표를 한 페이지에 담았어요"
   - CTA: "학급 소식 보러가기" (Primary) · "담임선생님과 이야기" (Ghost)
   - 배경: 복숭아→민트 파스텔 그라디언트 + 옅은 원 blur 장식
   - 상단 배지: "2026학년 1학기 기록 · 총 42개 활동"

2. 담임 인사말 (600자 이내)
   - 프로필 이미지(익명 실루엣) + 인사말 + 교육 철학 3줄

3. 이번 학기 핵심 프로젝트 3개
   - 카드 3열 그리드 (모바일 1열)
   - 각 카드: 이미지 / 제목 / 150자 요약 / "자세히 보기"
   - 예시 프로젝트:
     a) "우리 마을 쓰레기 지도" (사회·환경)
     b) "교실 화분 60일 일지" (과학·관찰)
     c) "친구 칭찬 릴레이" (국어·인성)

4. 학생 한 줄 소감 캐러셀 (6–8개 익명)
   - 별명 + 한 줄 + 파스텔 배경 카드
   - 자동 슬라이드 5초

5. 학부모 FAQ (아코디언 5개)
   - "과제는 어떻게 확인하나요?"
   - "담임선생님께 연락은 어떻게 하나요?"
   - "현장학습 일정은 어디에서 확인하나요?"
   - ...

6. 담임 연락 섹션
   - 쪽지 폼 (이름 · 학번 · 내용) — 제출은 Google Form iframe 또는 mailto
   - 공식 이메일 · 카카오 단톡방 QR

## 콘텐츠 규칙
- 학생 실명·사진 금지. 별명(초록 ★, 햇살 ☀️)과 아바타 실루엣만
- 이미지는 모두 Unsplash URL(`https://images.unsplash.com/photo-...`) 또는 Imagen 프롬프트 주석
- CTA는 페이지당 Primary 1개

## 기술 요구
- 단일 `index.html` + Tailwind CDN + Pretendard CDN + Iconify Solar
- 접근성: 모든 이미지 alt, WCAG AA 대비, 키보드 탭 순서 자연스럽게
- 모바일 360px부터 데스크톱 1440px까지 반응형

## 산출물
- `index.html` (완결, 플레이스홀더 없음)
- GitHub 저장소 생성 가이드 주석 상단
- 배포 URL: `https://hangang-class-4-3.vercel.app` (예상)
````

## 예상 결과물

- Hero 스크롤 시 fade-up
- 프로젝트 카드 hover 시 2px 상승 + 그림자 강화
- FAQ 펼칠 때 smooth 0.3s
- 담임 연락처는 스크롤 바닥 고정 mini CTA

## 배포 흐름

1. Stitch 결과 HTML → 로컬 `class-4-3/` 폴더에 저장
2. `git init · git add · git commit -m "학급 홍보 페이지 초안"`
3. GitHub → `new repo: hangang-class-4-3` → push
4. Vercel → Import → Deploy
5. URL 공유
