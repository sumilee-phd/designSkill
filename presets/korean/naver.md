# Naver 스타일 디자인 시스템

## 1. Visual Theme & Atmosphere
- **무드**: 한국 대표 포털 · 정보 밀도 높음 · 실용·신뢰
- **키워드**: 초록 · 정보 · 기능적 · 검색
- **철학**: "많은 정보를 깔끔하게, 찾기 쉽게"

## 2. Color Palette & Roles
- 네이버 그린 `#03C75A` — Primary
- 다크 그린 `#03A554` — Primary Hover
- 잉크 `#222222` — Text Primary
- 스틸 `#4B4B4B` — Text Secondary
- 라이트 그레이 `#767676` — Text Tertiary
- 라인 `#DADADA` — Border
- BG `#FAFAFA`
- Surface `#FFFFFF`
- 빨강 포인트 `#F4002B` (뉴스·알림)

## 3. Typography Rules
- 기본: Pretendard Variable (원래는 Naver 나눔스퀘어/Pretendard 혼용)
- Display 36 · H1 24 · H2 18 · H3 16 · Body 15 · Small 13 · Caption 11
- 굵기: Bold 700 / Regular 400
- line-height: 1.5

## 4. Component Stylings
- **Button Primary**: `#03C75A` · 라운드 4px · padding 12×20 · Bold
- **Button Secondary**: 흰 배경 · 테두리 `#03C75A` · 텍스트 `#03C75A`
- **Card**: 라운드 8px · 테두리 1px `#DADADA` · 그림자 최소
- **Input**: 라운드 4px · 테두리 1px · 포커스 `#03C75A`
- **Tag**: 라운드 4px · 배경 `#F1F8F4` · 텍스트 `#03A554`
- **Table**: zebra striping · header 배경 `#F5F5F5`

## 5. Layout Principles
- 정보 밀도 높음 — 섹션 간격 32–48px (다른 프리셋보다 좁음)
- 그리드: 16열 (정밀한 정보 배치)
- Max-width: 1080–1240px

## 6. Depth & Elevation
- 그림자 **거의 사용 안 함** — 테두리로 계층 구분
- L1만 사용: `0 2px 4px rgba(0,0,0,0.04)`

## 7. Do's and Don'ts
✅ 테두리 기반 카드 · 정보 밀도 중시 · 명확한 링크 색
❌ 과도한 여백 · 장식적 그림자 · 느린 모션

## 8. Responsive Behavior
- 데스크톱 우선 (전통적 포털 감각)
- 768+ : 2–3컬럼 · 1024+ : 3–4컬럼 복잡 레이아웃
- 모바일: 단일 컬럼 + 탭 네비

## 9. Agent Prompt Guide
> "네이버 스타일: Pretendard · 네이버 그린 `#03C75A` · 정보 밀도 높은 레이아웃 · 테두리 기반 · 실용적 · 장식 최소."
