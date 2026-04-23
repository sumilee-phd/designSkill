# 퀴즈 플레이풀 스타일 🎮

> **연수 오리지널 · 수업용 퀴즈·게임 앱 · 활기·즉각 피드백**

## 1. Visual Theme & Atmosphere
- **무드**: Kahoot·Duolingo 감성 · 신나는 미션 · 즉각적 보상
- **키워드**: 비비드 · 게임화 · 카운트다운 · 효과음 · 이모지
- **철학**: "정답보다 과정이 즐거워야 한다"

## 2. Color Palette & Roles
- 플레이 바이올렛 `#7C3AED` — Primary
- 라이트 퍼플 `#DDD6FE` — Surface Accent
- 정답 그린 `#22C55E` — Success
- 오답 레드 `#EF4444` — Danger
- 카운트다운 오렌지 `#F97316` — Warning
- 힌트 옐로우 `#FACC15`
- 배경 딥 바이올렛 `#2D1B69` (옵션: 게임 모드)
- BG 라이트 `#FAFAFA` (기본 모드)
- 잉크 `#1E1B4B` / `#F5F3FF` (다크)

## 3. Typography Rules
- 기본: Pretendard Variable
- 숫자: **Fredoka** 또는 Pretendard Black
- Display 72 · H1 48 · H2 32 · H3 24 · Body 18 · Small 14
- 질문 텍스트: 28–36px, Bold
- 카운트다운 숫자: 120px Black
- letter-spacing: 0 (질문은 명료)
- line-height: 1.3

## 4. Component Stylings
- **Answer Button**: 4개 컬러(A=빨강, B=파랑, C=노랑, D=초록) · 라운드 16px · padding 20×32 · 큰 글씨
- **Correct Animation**: 정답 시 버튼 스케일 1.05 + 초록 반짝
- **Wrong Animation**: 오답 시 shake + 빨강 반짝
- **Timer**: 원형 진행바 · 색 단계 전환 (초록 → 주황 → 빨강)
- **Score Badge**: 숫자 크게 · 별·트로피 아이콘
- **Confetti**: 정답 시 색종이 애니메이션 (일정 이상 점수)

## 5. Layout Principles
- 단일 질문 = 단일 화면 (집중)
- 중앙 정렬 · 세로 리듬
- 답 버튼 4개: 데스크톱 2×2 · 모바일 세로 4열
- 최대 폭 960px

## 6. Depth & Elevation
- 버튼 입체: `box-shadow: 0 6px 0 rgba(0,0,0,0.2)` — 눌림 시 4px 내려가는 효과
- 카드 hover: scale 1.02

## 7. Do's and Don'ts
✅ 컬러풀하게 · 애니메이션 충분히 · 효과음 호환 · 즉각 피드백
✅ 이모지 적극 활용 (🎯 🏆 ⚡ 💡)
❌ 차분한 파스텔만으로 · 느린 전환 · 작은 글씨
❌ 오답 공격적 연출(X 큰 표시 등)은 자신감 저하 → "다시 해볼까요" 톤

## 8. Responsive Behavior
- 모바일 우선 (스마트폰 퀴즈 환경)
- 터치 타겟 **64×64 이상**
- 가로모드도 대응

## 9. Agent Prompt Guide
> "퀴즈 플레이풀: Pretendard · 바이올렛`#7C3AED`+정답 그린·오답 레드 · 4색 답 버튼 · 라운드 16 · 눌림 효과 · 카운트다운 원형 · 즉각 피드백 애니메이션 · 이모지 환영."

## 🏫 마이크로카피 예시
```text
Hero: "오늘의 퀴즈를 시작할 준비 되었나요?"
Start: "시작하기 🎯"
Correct: "정답이에요! ⚡"
Wrong: "아쉬워요, 다시 해볼까요?"
Time's up: "시간이 다 됐어요! ⏰"
Final: "오늘도 잘했어요! 🏆 {score}점 획득"
Share: "친구에게 공유하기"
```
