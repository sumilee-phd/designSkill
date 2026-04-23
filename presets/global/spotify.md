# Spotify 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 네온 뮤직 · 다크 기본 · 에너제틱
- **키워드**: 블랙 · 네온 그린 · 앨범아트 · 리듬감
- **철학**: "음악은 색이다. 색은 감정이다."

## 2. Color Palette & Roles
- Spotify Black `#121212` — BG
- Deep Black `#000000`
- Spotify Green `#1DB954` — Primary Accent
- Bright Green `#1ED760` — Hover
- 텍스트 화이트 `#FFFFFF`
- 텍스트 2 `#B3B3B3`
- 서피스 2 `#181818` / `#282828` (호버)
- 라인 `#404040`

## 3. Typography Rules
- 기본: **Circular Std / Inter** + Pretendard
- Display 96 · H1 56 · H2 32 · H3 22 · Body 14 · Small 12
- 제목: Bold 700 + tight tracking
- 본문은 작고 조밀 (음악 앱 특유)

## 4. Component Stylings
- **Button Primary**: 그린 `#1DB954` · 라운드 full · padding 16×32 · 그린 글로우 hover
- **Button Ghost**: 투명 · 테두리 `#FFFFFF` · 호버 시 흰 배경 반전
- **Card**: 배경 `#181818` · 호버 `#282828` · 라운드 8px
- **Album Cover**: 정사각 · 그림자 블랙 `0 8px 24px rgba(0,0,0,0.5)`
- **Play Button**: FAB 원 · 그린 배경 · 검은 재생 아이콘

## 5. Layout Principles
- 그리드: 4–6열 앨범 카드
- 섹션 간격 48px
- 좌측 사이드바 네비게이션

## 6. Depth & Elevation
- 모든 카드에 검은 그림자
- 호버 시 살짝 상승 (`translateY(-4px)`)
- 네온 글로우: `box-shadow: 0 0 30px rgba(29,185,84,0.5)` (CTA)

## 7. Do's and Don'ts
✅ 다크 배경 + 네온 그린 포인트 · 앨범아트 큼직 · 에너지
❌ 밝은 배경 · 연한 파스텔 · 장식적 세리프

## 8. Responsive Behavior
- 모바일 하단 네비 · 앨범 카드 2–3열
- 터치 타겟 48×48

## 9. Agent Prompt Guide
> "스포티파이 스타일: 블랙 배경 `#121212` · 네온 그린 `#1DB954` · Circular+Pretendard · 앨범 그리드 · 음악 감각 · 다크 온리."
