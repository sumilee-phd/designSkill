# Stitch 프롬프트 템플릿

> 아래를 복사해 필요한 부분만 채운 뒤, Stitch·Claude·Gemini에 붙여넣으세요.

```text
@SKILL.md
@presets/[프리셋 경로].md 참조
DIALS: VARIANCE=?, MOTION=?, DENSITY=?

# 프로젝트: [프로젝트 이름]

## 목적
[한 두 문장으로 이 페이지·앱을 왜 만드는지, 누구를 위해 만드는지]

## 페이지 구조
1. [섹션 이름] ([높이/비율])
   - [주요 요소 1]
   - [주요 요소 2]
   - CTA: "[버튼 문구]"
2. ...

## 컨텐츠 예시 (플레이스홀더 금지 — 진짜 한국어로)
- Hero 타이틀: "..."
- 서브: "..."
- Primary CTA: "..."
- Secondary CTA: "..."

## 기술 요구
- 출력: [단일 HTML / Vite+React / Next.js]
- Tailwind CDN · Pretendard · Iconify Solar
- 반응형: [360px 모바일부터 1440px까지]

## 제약 / 금지
- 학생 실명·개인정보 금지
- Lorem Ipsum 금지
- 영어 플레이스홀더 금지
- [그 외 프로젝트 특수 제약]

## 접근성
- WCAG AA 이상 색 대비
- 키보드 탐색
- alt 텍스트 모든 이미지
- `prefers-reduced-motion` 존중

## 산출물
- [구체적으로 어떤 파일/URL을 받고 싶은지]
```
