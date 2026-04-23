# 학부모 안내 공식 스타일 🏛️

> **연수 오리지널 · 가정통신문·학부모 안내 · 신뢰·공식**

## 1. Visual Theme & Atmosphere
- **무드**: 학교 공문의 신뢰감 + 현대적 가독성
- **키워드**: 차분 · 단정 · 여백 · 격식
- **철학**: "학부모가 3분 안에 읽고, 안심할 수 있어야 한다"

## 2. Color Palette & Roles
- 딥 네이비 `#1E2A4B` — Primary (헤더·공식 요소)
- 스틸 블루 `#3B5178` — Primary Soft
- 잉크 `#1F2937` — Text Primary
- 차콜 `#4B5563` — Text Secondary
- 쿨 그레이 `#9CA3AF` — Tertiary
- 라인 `#E5E7EB`
- BG `#FAFBFC`
- 서피스 `#FFFFFF`
- 중요 강조 `#B91C1C` (극히 제한적 사용 — 긴급 공지)
- 안심 그린 `#059669` (확인 · 정상)

## 3. Typography Rules
- 기본: Pretendard Variable
- 공식 문서 느낌 강조 시: **Noto Serif KR** (제목만, 선택)
- Display 40 · H1 28 · H2 22 · H3 18 · Body 17 · Small 15 · Caption 13
- 본문: Regular 400 · line-height 1.8
- 제목: Semibold 600 (Bold는 강조 피하기)
- letter-spacing: -0.015em

## 4. Component Stylings
- **Button Primary**: `#1E2A4B` · 라운드 6px · padding 12×20 (작은 라운드)
- **Button Ghost**: 테두리 1px `#1E2A4B` · 호버 시 배경 채움
- **Card**: 라운드 8px (작게) · 테두리 1px · padding 32 (여백 넉넉)
- **Info Box**: 왼쪽 4px 세로선 + 옅은 배경 · 아이콘 + 본문 · 공지 강조용
- **일정 테이블**: 헤더 `#F3F4F6` · zebra 없음 · 깔끔한 정렬
- **Signature Block**: 하단 우측 · "○○ 초등학교 4학년 부장 김○○ 올림"

## 5. Layout Principles
- 본문 폭 **760px** (공문 느낌)
- 섹션 간격 48–64px
- 좌측 정렬 · 중앙 정렬 **금지** (공식 문서 감각)
- 헤더는 상단 중앙 · 로고 · 발신 날짜 · 제목

## 6. Depth & Elevation
- 그림자 **최소화** — 테두리 기반
- L1: `0 1px 2px rgba(0,0,0,0.03)` (거의 안 보임)

## 7. Do's and Don'ts
✅ 격식 있는 한국어 (~하시기 바랍니다, ~드립니다)
✅ 날짜·시간·연락처 명확히 · 발신 주체 명시 · 서명 블록
❌ 이모지 · 그라디언트 · 애니메이션
❌ 경쾌한 복숭아·파스텔 · 반말체 · 영어 혼용

## 8. Responsive Behavior
- 모바일: 본문 폭 자연 축소 · 여백 유지
- 프린트 대응 CSS 권장 (`@media print`)

## 9. Agent Prompt Guide
> "학부모 공식: Pretendard · 딥네이비 `#1E2A4B` · 본문 폭 760px · 격식 한국어 · 테두리 기반 카드 · 그림자 최소 · 이모지·애니메이션 금지 · 공문 감각."

## 🏫 마이크로카피 예시
```text
헤더: "○○초등학교 4학년 3반 담임 김○○ 드림"
제목: "2026학년도 봄 현장학습 안내"
본문 첫 줄: "안녕하십니까. 신록이 무르익는 5월입니다."
CTA: "참가 신청서 작성하기" · "전체 일정 안내 (PDF)"
긴급: "⚠ 우천 시 일정 변경 있을 수 있습니다"
맺음: "감사합니다."
```
