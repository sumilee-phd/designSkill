# Stripe 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 개발자 친화 핀테크 · 화려한 그라디언트 · 기술적
- **키워드**: 퍼플·블루 그라디언트 · 3D 카드 · 코드 표시
- **철학**: "개발자에게 사랑받는 프리미엄 인프라"

## 2. Color Palette & Roles
- Stripe Purple `#635BFF` — Primary
- Stripe Blue `#0A2540` — Dark Primary / Ink
- 그라디언트 A: `linear-gradient(135deg, #635BFF, #00D4FF)` — Primary
- 그라디언트 B: `linear-gradient(135deg, #A27BF6, #EB73FF)` — Accent
- BG `#FFFFFF` · BG 2 `#F6F9FC`
- 텍스트 `#0A2540` / `#425466`
- 라인 `#E6EBF1`

## 3. Typography Rules
- 기본: **Sohne / Inter** + Pretendard
- Display 64 · H1 40 · H2 28 · H3 20 · Body 17 · Code 15 (mono)
- 코드: JetBrains Mono / Fira Code
- 제목 letter-spacing: -0.02em

## 4. Component Stylings
- **Button Primary**: 그라디언트 A · 라운드 8px · padding 12×20
- **Button Ghost**: 흰 배경 · 테두리 `#E6EBF1`
- **Card**: 라운드 16px · 살짝 입체 그림자 · 호버 시 3D 틸트
- **Code Block**: 다크 `#0A2540` 배경 · 구문 하이라이트
- **Tab**: 언더라인 active + 그라디언트 선

## 5. Layout Principles
- Max-width 1280px
- 섹션 간격 120px
- 복잡한 비주얼(3D 카드·페이먼트 폼 미니어처) 사용

## 6. Depth & Elevation
- L1: `0 2px 6px rgba(10,37,64,0.05)`
- L2: `0 15px 35px rgba(99,91,255,0.15)` — 퍼플 글로우
- 3D: `transform: perspective(1000px) rotateY(-8deg)` — 카드 기울이기

## 7. Do's and Don'ts
✅ 그라디언트 대담하게 · 코드 미학 · 3D 카드 연출
❌ 너무 가벼운 파스텔 · 플랫 디자인 · 회색 주도

## 8. Responsive Behavior
- 모바일: 3D 효과 단순화, 카드 직립
- 터치 타겟 48×48

## 9. Agent Prompt Guide
> "스트라이프 스타일: 퍼플·블루 그라디언트 · Inter+Pretendard · 3D 기울인 카드 · 코드 블록 다크 · 개발자 미학."
