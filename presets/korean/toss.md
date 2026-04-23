# Toss 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 신뢰감 있고 친근한 핀테크 · 한국인 맞춤 UX
- **키워드**: 명료 · 직관 · 볼드한 숫자 · 미니멀
- **철학**: "송금보다 쉬운 디자인. 누구나 3초 안에 이해한다."

## 2. Color Palette & Roles
- 토스 블루 `#3182F6` — Primary · 주 CTA
- 딥 네이비 `#191F28` — Text Primary · 제목
- 미디엄 그레이 `#4E5968` — Text Secondary · 설명
- 라이트 그레이 `#8B95A1` — Text Tertiary · 메타
- 소프트 라인 `#E5E8EB` — Border
- 배경 `#F9FAFB` — Background
- 서피스 `#FFFFFF` — Surface
- 성공 `#00C853` — Success
- 경고 `#FFB300` — Warning
- 위험 `#F04452` — Danger

## 3. Typography Rules
- 기본: Pretendard Variable
- Display 48 · H1 32 · H2 24 · H3 20 · Body 17 · Small 14 · Caption 12
- 숫자 강조: 40–120px Black 900 · tabular-nums
- letter-spacing: -0.025em (제목) / -0.01em (본문)
- line-height: 1.6 (본문) / 1.3 (제목)

## 4. Component Stylings
- **Button Primary**: `#3182F6` · 라운드 12px · padding 16×24 · Bold · hover 명도 -5%
- **Button Secondary**: 배경 `#F2F4F6` · 텍스트 `#191F28`
- **Card**: 흰 배경 · 라운드 20px · shadow `0 4px 12px rgba(0,0,0,0.05)` · padding 24
- **Input**: border-bottom 2px 스타일 · 포커스 시 `#3182F6`
- **Badge**: 라운드 8px · 배경 `rgba(49,130,246,0.1)` · 텍스트 `#3182F6`

## 5. Layout Principles
- 그리드: 4열(모바일) · 12열(데스크톱)
- Max-width: 768px (모바일 우선 감성)
- 섹션 간격: 64–96px
- 패딩 20 (모바일) · 40 (데스크톱)

## 6. Depth & Elevation
- L0: 플랫
- L1: `0 4px 12px rgba(0,0,0,0.05)` — 기본 카드
- L2: `0 8px 24px rgba(49,130,246,0.12)` — hover · 강조
- L3: `0 16px 48px rgba(0,0,0,0.12)` — 모달

## 7. Do's and Don'ts
✅ 숫자는 크고 과감하게 · 한국어 자연 줄바꿈 · CTA는 페이지당 1개
❌ 복잡한 그라디언트 · 3개 이상의 컬러 악센트 · 작은 본문(14px 미만)

## 8. Responsive Behavior
- 모바일 우선 설계. 640px 이하에서 단일 컬럼, CTA Sticky Bottom
- 768+: 2컬럼 · 1024+: 3컬럼
- 터치 타겟 48×48px

## 9. Agent Prompt Guide
> "토스 스타일: Pretendard · 토스 블루 `#3182F6` 중심 · 숫자 볼드 · 미니멀 · 라운드 12px · 모바일 우선."
