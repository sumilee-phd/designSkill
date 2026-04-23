# Apple 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 프리미엄 · 타이포 중심 · 제품이 주인공
- **키워드**: 흰 배경 · 거대 타이포 · 중앙 정렬 · 정적
- **철학**: "제품이 말하게 한다. 장식은 방해한다."

## 2. Color Palette & Roles
- BG `#FFFFFF` (밝은 모드) · `#000000` (다크 모드)
- 텍스트 `#1D1D1F` — Primary (Apple Ink)
- 텍스트 2 `#6E6E73` — Secondary
- 라인 `#D2D2D7`
- 블루 `#0066CC` — 링크만
- Surface 2 `#F5F5F7` — 섹션 구분
- Success `#28CD41`

## 3. Typography Rules
- 기본: **SF Pro Display / Text** (fallback: Pretendard Variable)
- Display **96px** — 거대한 히어로 타이틀
- H1 56 · H2 40 · H3 24 · Body 19 · Caption 14
- letter-spacing: -0.05em (히어로) / -0.02em (본문)
- line-height: 1.05 (히어로) / 1.5 (본문)
- 제목은 Semibold 600, 본문 Regular 400

## 4. Component Stylings
- **Button Primary**: 블루 `#0066CC` · 라운드 full · padding 14×22 · 작은 크기
- **Button Ghost**: 텍스트 + 작은 화살표 `›` (hover시 오른쪽 이동)
- **Card**: 흰 배경 · 라운드 18px · 넉넉한 padding 40
- **이미지**: 둥근 모서리 18px · 그림자 없음

## 5. Layout Principles
- 중앙 정렬 히어로 · Max-width 1240px
- 섹션 간격 **160–200px** (매우 넓음)
- 제품 이미지는 화면의 2/3 점유 허용

## 6. Depth & Elevation
- 그림자 **극도로 미세**
- L1: `0 4px 16px rgba(0,0,0,0.04)`
- 주로 배경 색 변화(`#F5F5F7`)로 섹션 구분

## 7. Do's and Don'ts
✅ 여백을 위협적일 만큼 · 타이포가 히어로 · 제품 사진 대형
❌ 복잡한 그리드 · 장식 요소 · 강한 색 조합

## 8. Responsive Behavior
- 모바일: 히어로 타이틀 44–60px로 축소 유지
- 넓은 여백 유지 (최소 24px)

## 9. Agent Prompt Guide
> "애플 스타일: SF Pro+Pretendard · 거대 중앙 타이포 · 흰 배경 · 극도의 여백 · 제품 사진 중심 · 장식 없음."
