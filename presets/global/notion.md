# Notion 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 올인원 워크스페이스 · 에디토리얼 · 지적
- **키워드**: 모노크롬 · 에디터 · 구조 · 블록
- **철학**: "정보는 계층으로, 디자인은 내용의 뒤에"

## 2. Color Palette & Roles
- 잉크 `#37352F` — Text Primary
- 텍스트 2 `#787774` — Secondary
- 텍스트 3 `#9B9A97` — Tertiary
- BG `#FFFFFF`
- BG 2 `#F7F6F3` — 섹션 구분
- 회색 라인 `#E9E9E7`
- 블루 악센트 `#2383E2` — 링크만
- 빨강 경고 `#E03E3E`
- 노랑 하이라이트 `#FBE4A0`

## 3. Typography Rules
- 본문: Pretendard + 'iA Writer Quattro' / 'Inter' 혼합
- Display 48 · H1 32 · H2 24 · H3 20 · Body 17 · Small 14
- line-height: 1.7 (본문 읽기)
- 굵기: Semibold 600 (제목) / Regular 400 (본문)

## 4. Component Stylings
- **Button Primary**: 잉크 `#37352F` · 흰 텍스트 · 라운드 4px · padding 8×14 (작음)
- **Block**: 호버 시 왼쪽 `+` 아이콘 출현
- **Toggle Block**: ▸ 삼각형 · 클릭 시 펼침
- **Callout**: 배경 `#F1F1EF` · 이모지 + 텍스트 · 라운드 4px
- **Input**: 테두리 없음 · 배경 변화만 · 포커스 시 `#F7F6F3`

## 5. Layout Principles
- 본문 폭 680–740px 고정 (읽기 이상적)
- 사이드바 240px + 본문 나머지
- 섹션 간격: 24–32px (블록 간격)

## 6. Depth & Elevation
- 그림자 거의 없음
- L1: `0 1px 3px rgba(0,0,0,0.05)` — 드롭다운 정도만

## 7. Do's and Don'ts
✅ 읽기 중심 · 공백을 정보 구조로 · 블록 단위 편집
❌ 화려한 그라디언트 · 3개 이상 색 · 중앙 정렬 하이로

## 8. Responsive Behavior
- 모바일: 사이드바 접힘 · 본문 여백 16–20
- 768+: 사이드바 고정
- 터치 타겟 40×40

## 9. Agent Prompt Guide
> "노션 스타일: Pretendard · 모노크롬 · 본문 폭 700px · 블록 기반 · 에디토리얼 · 장식 최소."
