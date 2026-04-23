# Vercel 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 순수한 흑백 · 기하 · 다크 우선
- **키워드**: 흑백 · 기하 · 디벨로퍼 툴 · 미니멀
- **철학**: "속도와 명료함"

## 2. Color Palette & Roles
- 완전 흑 `#000000` — BG (다크) / Text (라이트)
- 완전 백 `#FFFFFF` — Text (다크) / BG (라이트)
- 그레이 6 `#0A0A0A` — Surface Dark
- 그레이 5 `#1A1A1A` · 그레이 4 `#333333` · 그레이 3 `#666666` · 그레이 2 `#999999` · 그레이 1 `#E5E5E5`
- 악센트: 파랑 `#0070F3` (거의 안 씀) · 빨강 `#E00`
- 그라디언트: 블랙 to 틴트 블루 (`#000` → `#0A1538`)

## 3. Typography Rules
- 기본: **Inter / Geist** + Pretendard
- Display 80 · H1 48 · H2 32 · H3 22 · Body 16 · Mono 15
- letter-spacing: tight (-0.04em)
- 제목은 Regular 400도 허용 (얇음)

## 4. Component Stylings
- **Button Primary**: 흰 배경 · 검은 텍스트 (반전) · 라운드 6px · 얇은 굵기
- **Card**: 테두리 1px `#333` · 배경 투명 또는 `#0A0A0A` · 라운드 8px
- **Code**: 순수 모노스페이스 · 배경 `#0A0A0A` · 라운드 8px
- **Arrow Link**: `→` 뒤따르는 밑줄 링크

## 5. Layout Principles
- Max-width 1100px
- 섹션 간격 120px
- 그리드 패턴 배경 허용 (`bg-grid-small`)

## 6. Depth & Elevation
- 다크 모드에서 그림자 **금지** — 대신 보더
- 라이트 모드에서만 L1: `0 2px 4px rgba(0,0,0,0.06)`

## 7. Do's and Don'ts
✅ 흑백만 · 기하 패턴 · 모노스페이스 강조 · 다크 기본
❌ 컬러풀한 팔레트 · 라운드 큰 요소 · 장식 이모지

## 8. Responsive Behavior
- 다크/라이트 자동 전환 지원 권장
- 모바일 여백 16–24

## 9. Agent Prompt Guide
> "버셀 스타일: 흑백 · Inter+Pretendard · 다크 우선 · 기하 그리드 배경 · 모노스페이스 악센트 · 극단적 미니멀."
