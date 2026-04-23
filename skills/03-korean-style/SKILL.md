---
name: korean-style
description: Supanova 기반 한국어 UI 최적화 규칙. Pretendard 폰트, word-break keep-all, 한국어 CTA 패턴, Iconify Solar, Double-Bezel 카드 아키텍처를 전 프로젝트에 자동 주입.
source: uxjoseph/supanova-design-skill
language: ko
---

# 03. korean-style — 한국어 UI 최적화 엔진

## 왜 필요한가

AI가 만든 UI는 대부분 **영어 기준 타이포·줄바꿈 규칙**을 따릅니다. 그 결과 한국어를 넣으면:
- 어색한 위치에서 단어가 끊깁니다 ("안녕하세 / 요")
- 시스템 폰트가 들쭉날쭉 표시됩니다 (Windows: 맑은고딕, Mac: Apple SD)
- 버튼 문구가 번역투("지금 구매하세요!")가 됩니다

`korean-style` 은 이 세 가지를 **자동 해결**합니다.

## 자동 주입 CSS

모든 HTML 출력에 아래 `<style>` 또는 Tailwind 설정이 포함되어야 합니다.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable-dynamic-subset.css" />

<style>
  :root {
    --font-sans: 'Pretendard Variable', Pretendard, -apple-system, BlinkMacSystemFont,
                 system-ui, Roboto, 'Helvetica Neue', 'Segoe UI', 'Apple SD Gothic Neo',
                 'Noto Sans KR', 'Malgun Gothic', sans-serif;
  }
  html, body, * {
    font-family: var(--font-sans);
    word-break: keep-all;
    overflow-wrap: break-word;
  }
  /* 한국어 본문 가독성 */
  p, li, blockquote { line-height: 1.75; letter-spacing: -0.01em; }
  /* 제목은 더 조여서 임팩트 */
  h1, h2, h3, h4 { letter-spacing: -0.025em; line-height: 1.3; }
  /* 숫자는 고정폭으로 (출결·점수 정렬) */
  .tabular { font-variant-numeric: tabular-nums; }
</style>
```

## Tailwind 설정 (tailwind.config.js)

```js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Pretendard Variable', 'Pretendard', '-apple-system', 'sans-serif'],
      },
      letterSpacing: {
        korean: '-0.01em',
        'korean-tight': '-0.025em',
      },
    },
  },
};
```

## 한국어 CTA 패턴 사전

번역투 CTA를 **한국 사용자가 실제로 쓰는 말**로 교체하세요.

| ❌ 번역투 | ✅ 자연스러운 한국어 | 맥락 |
|---|---|---|
| "지금 시작하기" | "3분 만에 시작하기" | 학습 앱 |
| "무료로 가입하세요" | "무료로 시작하기" | 회원가입 |
| "더 알아보기" | "자세히 보기" / "어떻게 쓰나요?" | 기능 소개 |
| "제출하기" | "보내기" / "제출" | 폼 |
| "구매하기" | "신청하기" / "담기" | 교육 상품 |
| "Learn More" | "자세히" | 범용 |
| "Get Started" | "시작하기" / "둘러보기" | Hero |
| "Contact Us" | "문의하기" / "담임선생님께" | 연락 |

## 교사·학생용 CTA 특화

**교사 시점**
- "학급 소식 보러가기" · "출결 확인하기" · "과제 내주기" · "공지 보내기"

**학생 시점**
- "오늘의 미션 확인" · "내 포트폴리오 보기" · "친구에게 칭찬 남기기"

**학부모 시점**
- "우리 아이 활동 보기" · "담임선생님께 문의" · "가정통신문 보기"

## Double-Bezel 카드 아키텍처

평범한 카드를 프리미엄으로 만드는 한국 UI 패턴입니다.

```html
<!-- 겉 베젤: 배경과 미묘한 대비 -->
<div class="p-1 rounded-3xl bg-gradient-to-br from-white/60 to-slate-100/80
            shadow-[0_10px_40px_-10px_rgba(0,0,0,0.1)]">
  <!-- 속 베젤: 실제 카드 -->
  <div class="rounded-[1.25rem] bg-white p-8">
    <h3 class="text-2xl font-bold tracking-korean-tight">카드 제목</h3>
    <p class="mt-3 text-slate-600 leading-relaxed">한국어 본문은 이렇게 읽히기 편합니다.</p>
  </div>
</div>
```

## Iconify Solar 아이콘

일관된 아이콘을 위해 [Solar 아이콘 셋](https://icon-sets.iconify.design/solar/) 사용.

```html
<!-- 설치 -->
<script src="https://code.iconify.design/iconify-icon/2.1.0/iconify-icon.min.js"></script>

<!-- 사용 -->
<iconify-icon icon="solar:home-2-bold-duotone" width="24"></iconify-icon>
<iconify-icon icon="solar:user-bold-duotone" width="24"></iconify-icon>
<iconify-icon icon="solar:book-bold-duotone" width="24"></iconify-icon>
```

교사·교실 맥락에 자주 쓰이는 아이콘:
- `solar:book-bold-duotone` — 수업·학습
- `solar:users-group-rounded-bold-duotone` — 학급·모둠
- `solar:notebook-bold-duotone` — 과제·포트폴리오
- `solar:medal-star-bold-duotone` — 상장·성취
- `solar:chat-round-line-bold-duotone` — 쪽지·문의
- `solar:calendar-bold-duotone` — 시간표·일정

## 자주 쓰는 한국어 마이크로카피

```text
[로딩]
"잠시만 기다려 주세요…"
"불러오는 중이에요"

[빈 상태]
"아직 등록된 내용이 없어요"
"첫 번째로 시작해 보세요!"

[에러]
"문제가 생겼어요. 잠시 후 다시 시도해 주세요"
"네트워크 연결을 확인해 주세요"

[성공]
"저장되었어요"
"전송 완료!"

[확인]
"정말 삭제하시겠어요?" → 확인 버튼: "네, 삭제할게요" / 취소: "아니요"
```

## 참고

원본: [uxjoseph/supanova-design-skill](https://github.com/uxjoseph/supanova-design-skill)
폰트: [Pretendard](https://github.com/orioncactus/pretendard)
