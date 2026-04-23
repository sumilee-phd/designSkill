# Kakao 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 친근한 국민 메신저 감성 · 라운드·노란색의 따뜻함
- **키워드**: 말랑 · 친근 · 라운드 · 노랑 악센트
- **철학**: "누구나 쉽게, 친구처럼 다가가는 디자인"

## 2. Color Palette & Roles
- 카카오 옐로우 `#FEE500` — Primary · 핵심 CTA
- 다크 텍스트 `#191919` — Text Primary
- 카카오 브라운 `#4B2B1A` — Secondary (로고 전통색)
- 차콜 `#3B3B3B` — Text Secondary
- 쿨 그레이 `#8B8B8B` — Text Tertiary
- 페일 그레이 `#F7F7F7` — Background
- 서피스 `#FFFFFF`
- 성공 `#06C755`
- 경고 `#FFB020`
- 위험 `#EE4444`

## 3. Typography Rules
- 기본: Pretendard Variable
- Display 44 · H1 28 · H2 22 · H3 18 · Body 16 · Small 14 · Caption 12
- 메신저 특유의 **둥근 굵기 감각** — Bold 700을 주로 사용
- line-height: 1.5 (본문) / 1.25 (제목)

## 4. Component Stylings
- **Button Primary**: `#FEE500` 배경 · 검정 텍스트 · 라운드 full · padding 14×28
- **Button Secondary**: 흰 배경 · 테두리 1px `#DDDDDD`
- **Card**: 라운드 16px · 옅은 그림자 · padding 20
- **Chat Bubble**: 라운드 20px · 내 말풍선 `#FEE500` · 상대 `#FFFFFF` · 꼬리 생략
- **Input**: 라운드 12px · 배경 `#F7F7F7` · 포커스 테두리 `#FEE500`
- **Badge**: 라운드 full · 빨간 알림 점 `#EE4444`

## 5. Layout Principles
- 모바일 우선 · 메신저 감각의 **리스트 중심** 레이아웃
- 리스트 아이템 높이 72px · 아바타 48×48
- 섹션 간격 48–64px

## 6. Depth & Elevation
- L1: `0 2px 8px rgba(0,0,0,0.04)` — 리스트 카드
- L2: `0 8px 20px rgba(0,0,0,0.08)` — FAB · 모달
- Floating Action Button: 노랑 배경 · 60×60 · L2 그림자

## 7. Do's and Don'ts
✅ 라운드 크게 · 친근한 이모지 활용 · 노랑은 포인트만
❌ 채도 낮은 회색조 과다 · 각진 모서리 · 차가운 블루 주류화

## 8. Responsive Behavior
- 모바일 앱 감성이 우선 — 데스크톱도 중앙 정렬 좁은 폭(480–640px)
- 터치 타겟 56×56

## 9. Agent Prompt Guide
> "카카오 스타일: Pretendard · 카카오 옐로우 `#FEE500` 포인트 · 라운드 크게 · 말랑한 감각 · 메신저 리스트 UI · 친근한 말투."
