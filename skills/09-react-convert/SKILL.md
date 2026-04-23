---
name: react-convert
description: Stitch가 생성한 단일 HTML을 React 컴포넌트 시스템으로 변환. 디자인 토큰 일관성, 자동 검증, Vite·Next.js 호환 출력.
source: google-labs-code/stitch-skills
language: ko
---

# 09. react-convert — HTML → React 변환

## 언제 사용하나

- Stitch로 만든 `index.html` 을 **React 앱으로 확장**하고 싶을 때
- GitHub + Vercel 배포 파이프라인에 **Next.js/Vite** 를 쓰고 싶을 때
- 재사용 가능한 **컴포넌트 시스템**을 구축해 여러 페이지를 만들 때

## 변환 원칙

### ① 디자인 토큰 분리
HTML의 모든 Tailwind 값을 스캔 → 반복되는 색·간격·폰트를 **tokens.ts** 로 추출.

```ts
// src/tokens.ts
export const colors = {
  primary:   '#FF8A65',   // 복숭아
  secondary: '#FFB74D',   // 산호
  accent:    '#6366F1',
  bg:        '#FFF8F0',
  surface:   '#FFFFFF',
  text:      '#1F2937',
  textMuted: '#6B7280',
} as const;

export const radius = {
  sm: '0.5rem', md: '1rem', lg: '1.5rem', xl: '2rem', full: '9999px',
} as const;

export const shadows = {
  soft: '0 10px 40px -10px rgba(0,0,0,0.08)',
  lift: '0 20px 60px -15px rgba(0,0,0,0.15)',
} as const;
```

### ② 컴포넌트 분해 규칙

한 HTML을 아래 원칙으로 쪼갭니다.

- **페이지 컴포넌트** (`app/page.tsx` 또는 `src/App.tsx`): 섹션 조합만
- **섹션 컴포넌트** (`components/sections/Hero.tsx` 등): 한 섹션 = 한 파일
- **UI 컴포넌트** (`components/ui/Button.tsx`, `Card.tsx`): 반복 요소
- **레이아웃** (`components/Layout.tsx`): Header/Footer 포함

### ③ 폴더 구조 (Vite + React + Tailwind)

```
src/
├── main.tsx
├── App.tsx
├── tokens.ts
├── components/
│   ├── ui/
│   │   ├── Button.tsx
│   │   ├── Card.tsx
│   │   ├── Badge.tsx
│   │   └── Input.tsx
│   ├── sections/
│   │   ├── Hero.tsx
│   │   ├── Features.tsx
│   │   ├── Testimonials.tsx
│   │   └── FAQ.tsx
│   └── Layout.tsx
├── hooks/
│   └── useScrollReveal.ts
└── styles/
    └── globals.css
```

### ④ 예시 변환

**Before (HTML)**
```html
<button class="px-8 py-4 rounded-full bg-gradient-to-r from-orange-400 to-pink-500
               text-white font-semibold shadow-lg hover:-translate-y-0.5
               transition-all duration-300">
  학급 소식 보러가기
</button>
```

**After (Button.tsx)**
```tsx
import { ButtonHTMLAttributes, forwardRef } from 'react';
import { clsx } from 'clsx';

type ButtonProps = ButtonHTMLAttributes<HTMLButtonElement> & {
  variant?: 'primary' | 'secondary' | 'ghost';
  size?: 'sm' | 'md' | 'lg';
};

export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  ({ variant = 'primary', size = 'md', className, ...props }, ref) => {
    const base = 'inline-flex items-center justify-center font-semibold rounded-full transition-all duration-300';
    const sizes = {
      sm: 'px-4 py-2 text-sm',
      md: 'px-6 py-3 text-base',
      lg: 'px-8 py-4 text-lg',
    };
    const variants = {
      primary: 'bg-gradient-to-r from-orange-400 to-pink-500 text-white shadow-lg hover:-translate-y-0.5',
      secondary: 'bg-white text-slate-800 border border-slate-200 hover:border-slate-400',
      ghost: 'bg-transparent text-slate-700 hover:bg-slate-100',
    };
    return <button ref={ref} className={clsx(base, sizes[size], variants[variant], className)} {...props} />;
  },
);
Button.displayName = 'Button';
```

**사용**
```tsx
<Button variant="primary" size="lg">학급 소식 보러가기</Button>
```

## 변환 체크리스트

- [ ] 모든 반복 UI가 컴포넌트로 추출됐다
- [ ] tokens.ts 에서 하드코딩 색이 사라졌다
- [ ] `key` prop이 모든 list 렌더링에 있다
- [ ] 이미지는 `next/image` 또는 lazy loading 적용
- [ ] 클라이언트 컴포넌트는 `'use client'` 명시 (Next.js)
- [ ] SSR 안전성 확인 (window·document는 useEffect 내부)
- [ ] 접근성: alt · aria-label · 키보드 조작 유지
- [ ] 빌드 성공 (`npm run build`)

## 자동 검증

`scripts/validate.mjs` 를 실행해 토큰 일관성 검증:

```bash
node scripts/validate.mjs
# ✓ 모든 색은 tokens.ts 에서 참조됨
# ✗ Button.tsx:14 - 하드코딩 #FF0000 발견
# ✓ 모든 섹션에 export default 존재
```

## Gemini·Claude Code 호출 예시

```text
@skills/09-react-convert 로 index.html 을 Vite+React+Tailwind 프로젝트로 변환해.
- tokens.ts 분리
- 섹션별 컴포넌트화
- shadcn/ui는 쓰지 말고 순수 Tailwind로
```

## 참고

원본: [google-labs-code/stitch-skills/react-components](https://github.com/google-labs-code/stitch-skills/tree/main/skills/react-components)
