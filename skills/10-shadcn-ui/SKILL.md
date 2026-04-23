---
name: shadcn-ui
description: shadcn/ui 컴포넌트 시스템을 React 프로젝트에 통합. Radix UI 기반 접근성 컴포넌트 + Tailwind 토큰 커스터마이징 가이드.
source: google-labs-code/stitch-skills
language: ko
---

# 10. shadcn-ui — shadcn/ui 통합

## shadcn/ui란

**라이브러리가 아닌 "복사 가능한 컴포넌트 모음"**. 필요한 컴포넌트만 CLI로 복사해 프로젝트 소스에 포함. Radix UI 위에 Tailwind로 스타일링. **접근성 기본 완벽 지원**.

## 언제 쓰나

- 드롭다운·모달·탭·시트·토스트 같은 **접근성이 까다로운** UI가 필요할 때
- 자체 컴포넌트 시스템이 없는데 **프로덕션 품질**을 원할 때
- React 프로젝트에 교실 앱의 **복잡한 상호작용**(출결 체크, 학생 선택 등)을 넣을 때

## 설치 (Next.js 기준)

```bash
# 프로젝트 초기화 (아직 안 했다면)
npx create-next-app@latest my-class-app --typescript --tailwind --eslint

cd my-class-app

# shadcn 초기화
npx shadcn@latest init
# ✓ TypeScript · Default · Slate · CSS variables 선택

# 필요한 컴포넌트 추가
npx shadcn@latest add button card dialog input label select tabs toast
```

## 교실 앱에 자주 쓰는 컴포넌트

| 컴포넌트 | 교실 용도 |
|---|---|
| `Button` | 모든 CTA |
| `Card` | 학생·과제·자료 카드 |
| `Dialog` | 학생 상세 모달, 확인창 |
| `Tabs` | 과목별·학년별 전환 |
| `Select` | 학급·모둠 선택 |
| `Checkbox` | 출결 체크, 과제 완료 |
| `Toast` | 저장 완료, 전송 완료 알림 |
| `Avatar` | 학생 프로필 |
| `Badge` | "완료", "대기", "우수" 태그 |
| `Sheet` | 사이드 상세 패널 |
| `Calendar` | 수업일·행사일 |
| `Progress` | 학습 진도, 읽은 책 비율 |

## DESIGN.md 토큰을 shadcn 테마에 연결

shadcn은 `globals.css` 의 CSS 변수로 색을 관리. DESIGN.md 의 팔레트를 그대로 복사.

```css
/* src/app/globals.css */
@layer base {
  :root {
    --background: 38 100% 97%;      /* 파스텔 크림 */
    --foreground: 222 47% 11%;
    --primary: 14 100% 69%;         /* 복숭아 */
    --primary-foreground: 0 0% 100%;
    --secondary: 33 100% 75%;       /* 산호 */
    --muted: 210 40% 96%;
    --accent: 243 75% 59%;          /* 인디고 */
    --border: 214 32% 91%;
    --ring: 14 100% 69%;
    --radius: 1rem;                 /* 교실 테마는 라운드 크게 */
  }
}
```

## 교실용 출결 체크 컴포넌트 예시

```tsx
'use client';
import { useState } from 'react';
import { Checkbox } from '@/components/ui/checkbox';
import { Avatar, AvatarFallback, AvatarImage } from '@/components/ui/avatar';
import { Badge } from '@/components/ui/badge';
import { Card } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { toast } from 'sonner';

type Student = { id: string; name: string; avatar?: string };

export function AttendanceList({ students }: { students: Student[] }) {
  const [checked, setChecked] = useState<Set<string>>(new Set());

  const toggle = (id: string) => {
    setChecked(prev => {
      const next = new Set(prev);
      next.has(id) ? next.delete(id) : next.add(id);
      return next;
    });
  };

  const save = () => {
    toast.success('출결이 저장되었어요', {
      description: `출석 ${checked.size}명 / 전체 ${students.length}명`,
    });
  };

  return (
    <Card className="p-6">
      <header className="flex justify-between items-center mb-4">
        <h2 className="text-xl font-bold tracking-korean-tight">오늘의 출결</h2>
        <Badge>{checked.size} / {students.length}</Badge>
      </header>

      <ul className="space-y-2">
        {students.map(s => (
          <li key={s.id}
              className="flex items-center gap-3 p-3 rounded-lg hover:bg-muted cursor-pointer"
              onClick={() => toggle(s.id)}>
            <Checkbox checked={checked.has(s.id)} />
            <Avatar>
              <AvatarImage src={s.avatar} />
              <AvatarFallback>{s.name[0]}</AvatarFallback>
            </Avatar>
            <span className="flex-1 font-medium">{s.name}</span>
            {checked.has(s.id) && <Badge variant="secondary">출석</Badge>}
          </li>
        ))}
      </ul>

      <Button className="w-full mt-6" onClick={save}>
        출결 저장하기
      </Button>
    </Card>
  );
}
```

## 한국어 대응 팁

shadcn의 기본 영어 레이블·플레이스홀더를 한국어로 교체하는 체크리스트:

- [ ] `Dialog`: "Cancel" → "취소", "Continue" → "계속하기"
- [ ] `Select`: "Select an option" → "선택하세요"
- [ ] `Calendar`: 월/요일 이름 로컬라이즈 (`date-fns/locale/ko` 사용)
- [ ] `Command` (검색 팔레트): "No results" → "검색 결과가 없어요"
- [ ] `Toast`: default 텍스트 모두 한국어로
- [ ] Form 에러: zod 메시지 한국어로 (예: `z.string().min(1, '이름을 입력해 주세요')`)

## 참고

원본: [google-labs-code/stitch-skills/shadcn-ui](https://github.com/google-labs-code/stitch-skills/tree/main/skills/shadcn-ui)
공식: [shadcn/ui](https://ui.shadcn.com/)
