---
name: minimalist
description: Notion·Linear·Vercel 스타일의 에디토리얼 미니멀리즘. 모노크롬 기반, 타이포 중심, 정보 구조가 디자인이 되는 스타일.
source: Leonxlnx/taste-skill
language: ko
---

# 06. minimalist — 에디토리얼 미니멀

## 분위기

- **느낌**: Notion · Linear · Vercel · Substack · Posthog · Are.na
- **키워드**: 절제 · 타이포 중심 · 모노크롬 · 구조적 · 에디토리얼
- **적합 맥락**: 수업 자료 허브, 독서록, 교과 문서, 교사 블로그, 학생 에세이

## 핵심 규칙

### 색
```css
--bg:       #FFFFFF;           /* 순백 */
--bg-2:     #FAFAFA;           /* 옅은 회색 섹션 구분 */
--text:     #0A0A0A;           /* 거의 검정 */
--text-2:   #525252;
--text-3:   #A3A3A3;           /* 메타 텍스트 */
--border:   #E5E5E5;
--accent:   #0A0A0A;           /* 강조도 검정 */
--highlight:#FEF08A;           /* 노란 형광펜 (옵션) */
```

### 타이포그래피 (가장 중요)
- 본문: Pretendard Variable
- 헤딩: **같은 폰트지만 굵기로만 차별화** (Regular 400 · Medium 500 · Bold 700)
- 크기 스케일은 **4단계만** — H1 / H2 / Body / Small
- 본문 폭: 최대 680px (읽기 이상적 길이)
- line-height: 1.75 (본문), 1.3 (제목)

### 레이아웃
- 2컬럼 그리드 기본 (Sidebar 240 / Main 여백)
- 섹션 구분: 선 하나 `border-t border-neutral-200`
- 카드보다 **리스트/테이블** 선호

### 컴포넌트
- 버튼: 테두리만 `border border-neutral-900` · 라운드 최소(`rounded`) 또는 없음
- 링크: 밑줄 + 호버시 검은 배경
- 구분자: 8pt 점 • 또는 얇은 선

## Hero 템플릿

```html
<section class="max-w-2xl mx-auto px-6 py-24">
  <!-- 메타 태그 -->
  <div class="flex items-center gap-3 text-sm text-neutral-500 mb-4">
    <span>수업자료</span>
    <span>•</span>
    <time datetime="2026-05-21">2026년 5월 21일</time>
    <span>•</span>
    <span>이수미</span>
  </div>

  <!-- 타이틀 -->
  <h1 class="text-5xl font-bold tracking-korean-tight leading-tight mb-6">
    AI 시대 교실, 우리는 무엇을 가르쳐야 할까
  </h1>

  <!-- 리드 -->
  <p class="text-xl text-neutral-700 leading-relaxed mb-12">
    도구는 빠르게 바뀌지만, 질문하는 힘은 쉽게 낡지 않습니다.
    4학년 교실에서 6개월간 AI를 함께 써본 기록을 공유합니다.
  </p>

  <!-- 본문 -->
  <article class="prose prose-neutral max-w-none">
    <h2>1. 왜 AI 리터러시인가</h2>
    <p>...</p>
    <h2>2. 수업 설계의 3가지 원칙</h2>
    <p>...</p>
  </article>
</section>
```

## 리스트 스타일 (미니멀의 꽃)

```html
<ul class="divide-y divide-neutral-200">
  <li class="py-4 flex items-baseline gap-4">
    <span class="text-sm text-neutral-400 tabular-nums w-12">01</span>
    <div class="flex-1">
      <h3 class="font-semibold">수업용 웹앱 만들기</h3>
      <p class="text-sm text-neutral-600 mt-1">Stitch + Vercel 30분 실습</p>
    </div>
    <span class="text-sm text-neutral-400">5.21</span>
  </li>
  <!-- ... -->
</ul>
```

## 타이포그래피 하이라이트

```html
<!-- 강조 방식: 형광펜 -->
<p>이 수업의 핵심은 <mark class="bg-yellow-200 px-1 rounded-sm">질문</mark>입니다.</p>

<!-- 강조 방식: 굵게 + 검정 배경 -->
<span class="bg-black text-white px-2 py-0.5 font-semibold">필독</span>

<!-- 인용 -->
<blockquote class="border-l-4 border-black pl-6 italic text-xl text-neutral-800">
  "배움은 답을 쌓는 것이 아니라 질문을 정교하게 하는 것이다."
</blockquote>
```

## Do / Don't

✅ **Do**
- 여백을 위협적일 만큼 많이
- 정보 계층은 굵기·크기·색 3단계만
- 본문 글자 크기 18–20px (커 보여도 편함)
- 첫 문장은 항상 강력하게

❌ **Don't**
- 알록달록한 색 팔레트
- 그라디언트·그림자 (거의 없음)
- 아이콘 남발 (텍스트로 충분)
- 3개 이상의 폰트

## DIALS 권장값

```text
DIALS: VARIANCE=3, MOTION=2, DENSITY=3
```

## 참고

원본: [Leonxlnx/taste-skill — minimalist-skill](https://github.com/Leonxlnx/taste-skill)
