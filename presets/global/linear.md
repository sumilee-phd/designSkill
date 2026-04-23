# Linear 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 프리미엄 SaaS · 어두운 우주감 · 속도감
- **키워드**: 다크 · 그라디언트 · 블러 · 빠른 모션
- **철학**: "빠르게 움직이되, 우아하게"

## 2. Color Palette & Roles
- 배경 `#08090A` — Primary BG
- 서피스 `#151517` — Card
- 보더 `#1F2128` — Line
- 텍스트 `#F7F8F8` — Primary
- 텍스트 2 `#B4BBC4`
- 텍스트 3 `#62666D`
- Linear Blue `#5E6AD2` — Primary Accent
- 그라디언트 `linear-gradient(135deg, #5E6AD2 0%, #9E7AFF 50%, #FF6B9D 100%)`
- 성공 `#4CB782` · 경고 `#F2994A` · 위험 `#EB5757`

## 3. Typography Rules
- 기본: **Inter Variable** + Pretendard (한국어)
- Display 72 · H1 48 · H2 32 · H3 22 · Body 15 · Small 13
- tracking-tight · line-height: 1.4
- 제목은 그라디언트 텍스트 허용 (`bg-clip-text`)

## 4. Component Stylings
- **Button Primary**: `#5E6AD2` → `#9E7AFF` 그라디언트 · 라운드 8px · padding 10×16
- **Button Ghost**: `rgba(255,255,255,0.08)` 배경 · 테두리 `rgba(255,255,255,0.08)`
- **Card**: 서피스 `#151517` · 보더 1px `#1F2128` · 라운드 12px
- **Input**: 어두운 배경 · 포커스 시 테두리 `#5E6AD2` · 라운드 8px
- **Keyboard Key**: 작은 `<kbd>` 스타일 네온 하이라이트

## 5. Layout Principles
- Max-width: 1200–1400px
- 섹션 간격 160px (시네마틱)
- 비주얼에 공간 많이

## 6. Depth & Elevation
- 깊이는 **blur + glow** 로 표현:
  ```css
  box-shadow: 0 0 120px -20px rgba(94,106,210,0.4);
  ```
- 배경 blur 원: `filter: blur(80px)` 컬러 블롭

## 7. Do's and Don'ts
✅ 어두운 배경에 작은 텍스트 대비 확실히 · 그라디언트 텍스트 · 스크롤 기반 모션
❌ 밝은 배경 과다 · 플랫한 회색 카드 · 느린 전환

## 8. Responsive Behavior
- 모바일에서도 다크 유지
- 터치 타겟 44×44

## 9. Agent Prompt Guide
> "리니어 스타일: 다크 배경 `#08090A` · Inter+Pretendard · 블루→퍼플 그라디언트 · glow 효과 · 프리미엄 SaaS."
