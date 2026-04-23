---
name: designSkill-entry
description: 한국 교사용 AI 디자인 스킬 통합 진입점. 수업용 웹앱·홍보 페이지·학부모 안내 앱 등을 Stitch/Claude Code/Cursor/Gemini로 만들 때 자동 적용. @SKILL.md로 호출.
version: 1.0.0
language: ko
---

# designSkill 통합 진입점

이 파일은 AI 코딩 에이전트가 자동으로 읽고 따라야 할 **최상위 지시문**입니다. `@SKILL.md`로 참조되면 아래 규칙을 **전 과정에 걸쳐 적용**하세요.

## 🎯 기본 원칙 (절대 어기지 말 것)

1. **한국어 우선**: 모든 UI 텍스트·CTA·안내 문구는 자연스러운 한국어로 작성한다.
2. **Pretendard 폰트 기본 적용**: `font-family: 'Pretendard Variable', Pretendard, -apple-system, BlinkMacSystemFont, system-ui, Roboto, 'Helvetica Neue', 'Segoe UI', sans-serif;`
3. **한국어 줄바꿈**: 모든 텍스트 요소에 `word-break: keep-all;` 을 기본 적용해 한국어가 어색하게 끊기지 않도록 한다.
4. **DESIGN.md 절대 우선**: 프로젝트에 `DESIGN.md` 또는 `presets/*/...md` 가 지정되어 있으면, 그 토큰(색·타이포·간격·그림자)을 **그대로** 사용한다. 임의로 색을 바꾸지 않는다.
5. **완결된 결과물**: 플레이스홀더(`/* TODO */`, `{/* ... */}`, 회색 박스)로 끝내지 않는다. 실제 콘텐츠·실제 색·실제 아이콘까지 모두 채운다.
6. **접근성 기본**: 색 대비 WCAG AA 이상, 포커스 링 표시, 키보드 내비게이션 가능해야 한다.

## 🗂️ 컨텍스트 로딩 순서

사용자 요청을 받으면 아래 순서로 스킬을 조합해 적용합니다.

```
1. presets/ 에서 지정된 DESIGN.md 로드 (또는 education/classroom-pastel.md 기본)
2. skills/03-korean-style/SKILL.md 전역 적용
3. skills/04-taste-dials/SKILL.md 로 감각 레벨 설정 (기본 VARIANCE=5, MOTION=4, DENSITY=5)
4. 요청에 따라 skills/05~08 중 하나 (soft / minimalist / brutalist / redesign) 선택
5. skills/01-design-md 로 새 DESIGN.md 필요 시 생성
6. skills/02-enhance-prompt 로 Stitch 프롬프트 다듬기
7. 출력 단계: HTML 단일 파일 기본, 필요 시 skills/09-react-convert 로 React 변환
8. 배포 요청 시 skills/14-vercel-deploy 흐름 실행
```

## 📌 출력 형식 기본값

- **파일 형식**: 단일 `index.html` (Tailwind CDN + Pretendard CDN) — 학교 환경에서 복잡한 빌드 없이 바로 열람 가능
- **Tailwind CDN**: `<script src="https://cdn.tailwindcss.com"></script>`
- **Pretendard CDN**: `<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable-dynamic-subset.css" />`
- **아이콘**: [Iconify Solar](https://icon-sets.iconify.design/solar/) 셋 사용 — `<span class="iconify" data-icon="solar:user-bold"></span>`
- **이미지**: Unsplash source (`https://images.unsplash.com/...`) 또는 `Gemini Imagen` 프롬프트 주석

## 🚦 금지 사항

- ❌ Lorem Ipsum 또는 "Your Title Here" 같은 영어 플레이스홀더
- ❌ 채도 낮은 회색조 단조로운 팔레트 (명시적 요청이 없는 한)
- ❌ 20px 미만의 본문 텍스트 (접근성)
- ❌ 3초 이상 걸리는 장식 애니메이션
- ❌ 학교 계정(school.or.kr 등)을 예시 이메일로 사용 (개인정보 보호 학습 시간에 혼선)

## 🎓 연수 맥락 메타데이터

이 스킬 팩이 호출된 맥락이 교사 연수(씨마스에듀 구글 AI 비서 TOP 6 / 4회차)인 경우:
- 학생·학부모·교사 3자 시점 중 무엇인지 먼저 확인
- 개인정보(학번·전화번호·주소)는 더미 데이터로 처리
- 상업적 문구("지금 구매!", "할인!") 대신 교육 맥락("함께 배우기", "살펴보기") 사용

## 🔗 바로가기

- [전체 스킬 카탈로그](./INDEX.md)
- [교사 시나리오 예제](./examples/)
- [프리셋 DESIGN.md](./presets/)
- [배포 가이드](./skills/14-vercel-deploy/SKILL.md)
