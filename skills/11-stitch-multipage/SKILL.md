---
name: stitch-multipage
description: 단일 프롬프트로 여러 페이지를 가진 완전한 웹사이트를 Stitch로 자동 생성. 네비게이션 일관성·파일 구조 자동화·교차 링크 검증 내장.
source: google-labs-code/stitch-skills (stitch-loop)
language: ko
---

# 11. stitch-multipage — 멀티페이지 사이트 자동 생성

## 언제 사용하나

- 학급·동아리·학교를 소개하는 **다중 페이지 웹사이트** (메인/소개/활동/연락)
- 여러 과목의 수업자료를 **각각의 페이지**로 정리하고 싶을 때
- 행사 안내 사이트 (메인·일정·참가신청·FAQ)

## 생성되는 구조

```
my-class-site/
├── index.html             # 메인 (Hero + 간단 소개)
├── about.html             # 우리 반 소개
├── projects.html          # 프로젝트 · 활동 갤러리
├── students.html          # 학생 포트폴리오
├── contact.html           # 담임 연락 · 문의
├── 404.html               # 에러 페이지
├── assets/
│   ├── styles.css         # 공통 CSS (Pretendard · 토큰)
│   ├── script.js          # 공통 JS (네비·모션)
│   └── images/
└── DESIGN.md              # 전체 디자인 시스템
```

## 5단계 실행 프로세스

### ① 사이트맵 설계
사용자의 한 줄 요청을 받아 **페이지 목록 + 각 페이지 목적**을 먼저 정의.

```markdown
# 학급 사이트 사이트맵
- index.html     : 방문자 첫 인상 · 핵심 CTA (학급 소식 보기)
- about.html     : 담임 인사말 · 학급 철학 · 1년 계획
- projects.html  : 학기 프로젝트 3–6개 상세
- students.html  : 학생 소개 (익명) · 한 줄 소감 모음
- contact.html   : 담임 연락 · 학부모 FAQ · 문의 폼
```

### ② 공통 요소 정의
모든 페이지에 들어갈 **불변 요소**를 먼저 HTML 조각으로 작성.

```html
<!-- _header.html -->
<header class="fixed top-0 w-full glass z-50">
  <nav class="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
    <a href="/" class="font-bold text-lg">4학년 3반 🌱</a>
    <ul class="flex gap-6 text-sm">
      <li><a href="/about.html">반 소개</a></li>
      <li><a href="/projects.html">활동</a></li>
      <li><a href="/students.html">친구들</a></li>
      <li><a href="/contact.html">연락</a></li>
    </ul>
  </nav>
</header>
```

### ③ DESIGN.md 한 번만 작성
`skills/01-design-md` 로 **사이트 전체 공통** DESIGN.md 를 만들고, 각 페이지는 이것만 참조.

### ④ 페이지별 생성 (루프)
사이트맵의 각 페이지를 **순차적으로** Stitch/Gemini에 요청. 각 요청에 다음을 포함:

```text
@DESIGN.md 참조.
@_header.html 을 <body> 상단에 붙일 것.
@_footer.html 을 <body> 하단에 붙일 것.

이번 페이지는 [projects.html]:
- 목적: 한 학기 진행한 프로젝트 5개를 시각적으로 소개
- 섹션: Hero(페이지 제목) · 프로젝트 카드 5개 · 참여 갤러리 · 다음 페이지 링크
- 프로젝트 예: "우리 마을 쓰레기 지도", "교실 화분 일지", ...
```

### ⑤ 교차 링크 검증
모든 페이지 생성 후 자동 체크:

- [ ] 모든 `<a href="...">` 가 실제 파일을 가리킨다
- [ ] 헤더 네비의 모든 링크가 일관된다
- [ ] 404.html 이 존재하고, 홈으로 돌아가는 CTA가 있다
- [ ] 공통 스타일(styles.css)이 모든 페이지에 링크됐다

## 사용 예시

```text
사용자: @skills/11-stitch-multipage 로 "한강초 4학년 3반" 사이트 만들어줘.
      5페이지, 파스텔 교실 테마, 학부모도 보는 공식 성격.

AI:
[1/6] 사이트맵 생성 중... → 5페이지 확정
[2/6] DESIGN.md 작성 중... → presets/education/classroom-pastel.md 기반
[3/6] 공통 헤더/푸터 생성 중...
[4/6] index.html 생성 중... ✓
      about.html 생성 중... ✓
      projects.html 생성 중... ✓
      students.html 생성 중... ✓
      contact.html 생성 중... ✓
      404.html 생성 중... ✓
[5/6] 교차 링크 검증 중... ✓
[6/6] 완료! 총 6 파일, 압축 전송.
```

## 주의 사항

- 페이지 수는 **3–8개 권장**. 그 이상이면 CMS(예: Notion) 고려
- 이미지는 모두 Unsplash URL 또는 Imagen 생성 프롬프트 주석
- 폼 제출은 실제 백엔드 없이 **Google Form · Tally 링크**로 대체 권장
- 학생 실명 등장 금지. 익명 또는 이니셜만

## 참고

원본: [google-labs-code/stitch-skills/stitch-loop](https://github.com/google-labs-code/stitch-skills/tree/main/skills/stitch-loop)
