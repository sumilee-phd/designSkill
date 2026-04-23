# 🎨 designSkill — 내 교실을 바꾸는 AI 디자인 스킬 팩

> **대상**: 씨마스에듀 [내 교실을 바꾸는 최강 구글 AI 비서 TOP 6] 연수 수강 선생님 / AI 코딩 에이전트로 수업용 웹앱을 만드시는 모든 선생님
> **강사**: 이수미 · 김남희 (씨마스 주임 강사)
> **연수 4회차**: 2026.05.21.(목) 19:00–21:30 · *UI/UX 디자인부터 배포까지 상호작용 앱 완성* (Stitch · AI Studio · GitHub · Vercel)

---

## ✨ 왜 designSkill인가요?

AI 코딩 에이전트(Claude Code · Cursor · Gemini · Stitch)에게 그냥 “예쁘게 만들어줘”라고 하면 결과물은 언제나 밋밋합니다. **디자인 감각을 텍스트 파일로 주입**하면 같은 AI가 전혀 다른 퀄리티를 뽑아냅니다.

`designSkill`은 한국 교사의 수업 현장을 염두에 두고, 전 세계에 흩어져 있는 최고의 디자인 스킬들을 **하나의 패키지로 올인원 정리**한 것입니다.

- ✅ **15개 스킬** — Google Stitch 공식 · AI Studio Build · Taste-Skill · Supanova 한국어 · Figma · Vercel 배포까지
- ✅ **16개 프리셋 DESIGN.md** — Toss · Kakao · Notion · Linear · 교실용 파스텔 등 즉시 사용
- ✅ **10개 교사 시나리오 예제** — 학급 홍보 페이지부터 학부모 안내 앱까지
- ✅ **100% 한국어** — Pretendard 폰트, 한국어 CTA, `word-break: keep-all` 내장

---

## 🚀 30초 설치 · 사용법

### 1단계. 프로젝트에 스킬 복사
작업 중인 폴더 루트에 `designSkill/` 전체를 복사하거나, 필요한 스킬만 골라 넣으세요.

```bash
git clone https://github.com/sumilee-phd/designSkill.git
```

### 2단계. AI 에이전트에게 참조 지시
```text
# Claude Code / Cursor
@SKILL.md 를 참조해서 [학급 홍보 페이지]를 만들어줘.
스타일은 @presets/education/classroom-pastel.md 기준으로.

# Gemini / Stitch
SKILL.md 와 presets/korean/toss.md 를 참조해서 출결 확인 앱을 설계해줘.
```

### 3단계. 완성된 HTML/React 코드를 Stitch → GitHub → Vercel로 배포
상세 절차는 [`skills/14-vercel-deploy/SKILL.md`](./skills/14-vercel-deploy/SKILL.md) 참고.

---

## 📚 수록 스킬 한눈에 보기

| # | 스킬 | 한 줄 설명 | 출처 |
|---|---|---|---|
| 01 | [`design-md`](./skills/01-design-md/SKILL.md) | DESIGN.md 9섹션 자동 생성 (Stitch 공식 포맷) | Google Stitch-Skills |
| 02 | [`enhance-prompt`](./skills/02-enhance-prompt/SKILL.md) | 모호한 아이디어 → Stitch 최적화 프롬프트 | Google Stitch-Skills |
| 03 | [`korean-style`](./skills/03-korean-style/SKILL.md) | Pretendard · 한국어 줄바꿈 · CTA 패턴 | Supanova |
| 04 | [`taste-dials`](./skills/04-taste-dials/SKILL.md) | VARIANCE / MOTION / DENSITY 감각 다이얼 | Taste-Skill |
| 05 | [`soft-style`](./skills/05-soft-style/SKILL.md) | $150k 에이전시급 프리미엄 소프트 UI | Taste-Skill |
| 06 | [`minimalist`](./skills/06-minimalist/SKILL.md) | Notion / Linear 스타일 에디토리얼 | Taste-Skill |
| 07 | [`brutalist`](./skills/07-brutalist/SKILL.md) | 실험적 Swiss 타이포그래피 | Taste-Skill |
| 08 | [`redesign`](./skills/08-redesign/SKILL.md) | 기존 UI 개선 / 리디자인 | Taste-Skill |
| 09 | [`react-convert`](./skills/09-react-convert/SKILL.md) | Stitch HTML → React 컴포넌트 변환 | Google Stitch-Skills |
| 10 | [`shadcn-ui`](./skills/10-shadcn-ui/SKILL.md) | shadcn/ui 컴포넌트 통합 가이드 | Google Stitch-Skills |
| 11 | [`stitch-multipage`](./skills/11-stitch-multipage/SKILL.md) | 한 번에 다중 페이지 웹사이트 생성 | Google Stitch-Skills |
| 12 | [`remotion-video`](./skills/12-remotion-video/SKILL.md) | 앱 소개 영상 자동 제작 | Google Stitch-Skills |
| 13 | [`figma-import`](./skills/13-figma-import/SKILL.md) | Figma URL → 코드 변환 (선택) | OpenAI Skills |
| 14 | [`vercel-deploy`](./skills/14-vercel-deploy/SKILL.md) | GitHub → Vercel 배포 (교사용) | 오리지널 |
| 15 | [`ai-studio-build`](./skills/15-ai-studio-build/SKILL.md) | **★ Stitch UI에 실제 기능 이식 (Gemini API 연동)** | 연수 오리지널 |

## 🎨 수록 프리셋 DESIGN.md (16종)

**🇰🇷 한국 기업** — [`toss`](./presets/korean/toss.md) · [`kakao`](./presets/korean/kakao.md) · [`naver`](./presets/korean/naver.md) · [`line`](./presets/korean/line.md) · [`pinkoi`](./presets/korean/pinkoi.md)

**🌐 글로벌** — [`notion`](./presets/global/notion.md) · [`linear`](./presets/global/linear.md) · [`apple`](./presets/global/apple.md) · [`stripe`](./presets/global/stripe.md) · [`vercel`](./presets/global/vercel.md) · [`spotify`](./presets/global/spotify.md)

**🏫 교육용 오리지널** — [`classroom-pastel`](./presets/education/classroom-pastel.md) · [`lesson-clean`](./presets/education/lesson-clean.md) · [`quiz-playful`](./presets/education/quiz-playful.md) · [`parent-formal`](./presets/education/parent-formal.md) · [`student-vibrant`](./presets/education/student-vibrant.md)

## 🎯 교사 시나리오 예제 (10종)

[`examples/`](./examples/) 폴더에서 바로 복사해 사용할 수 있는 프롬프트 모음.

---

## 🗺️ 연수 4회차 권장 실습 흐름

```
┌─────────────────────────────────────────────────────────────┐
│ [1] AI Studio에서 아이디어 발상 · 기능 명세                 │
│                    ↓                                        │
│ [2] enhance-prompt + korean-style + 원하는 프리셋 결합      │
│                    ↓                                        │
│ [3] Stitch에서 화면 생성 → design-md 로 DESIGN.md 추출      │
│                    ↓                                        │
│ [4] stitch-multipage 로 다중 화면 UI 완성                   │
│                    ↓                                        │
│ [5] ★ AI Studio Build 로 실제 기능 구현                     │
│     (폼 제출 · 데이터 저장 · Gemini API 연동)              │
│                    ↓                                        │
│ [6] react-convert 로 React 코드화 (선택)                    │
│                    ↓                                        │
│ [7] GitHub push → vercel-deploy 로 실제 배포                │
│                    ↓                                        │
│ [8] remotion-video 로 홍보 영상 생성                        │
└─────────────────────────────────────────────────────────────┘
```

> 💡 **왜 AI Studio Build가 필요한가?**
> Stitch는 **UI·화면 디자인**에 특화되어 있지만, 실제 동작(폼 처리·API 호출·데이터 저장)은 구현하지 않습니다.
> AI Studio Build가 Stitch의 HTML을 받아 **진짜 앱**으로 바꿔줍니다.

---

## 📜 라이선스 · 출처

- **MIT License** — 자유롭게 사용·수정·재배포 가능
- **원본 저장소**:
  - [google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)
  - [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md)
  - [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
  - [uxjoseph/supanova-design-skill](https://github.com/uxjoseph/supanova-design-skill)
  - [oh-my-design.kr](https://oh-my-design.kr/)
  - [openai/skills — figma-implement-design](https://github.com/openai/skills/blob/main/skills/.curated/figma-implement-design/SKILL.md)

> *"AI를 가르치는 교사에서, AI로 수업을 혁신하는 교사로"*
