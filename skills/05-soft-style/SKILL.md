---
name: soft-style
description: $150k급 에이전시 감각의 프리미엄 소프트 UI 스타일. 차분한 대비·부드러운 그림자·유리같은 표면·고급 세리프 혼합.
source: Leonxlnx/taste-skill
language: ko
---

# 05. soft-style — 프리미엄 소프트

## 분위기

- **느낌**: Superhuman · Linear · Arc Browser · Raycast · Attio
- **키워드**: 차분 · 고급 · 부드러움 · 반투명 · 호흡
- **적합 맥락**: 학교 소개 페이지, 교원 포트폴리오, 고학년 학습 앱, 교육 컨퍼런스

## 핵심 규칙

### 색 (Palette)
```css
--bg:        #F8F7F4;           /* 따뜻한 오프화이트 */
--surface:   #FFFFFF;
--surface-2: rgba(255,255,255,0.6); /* 유리 효과용 */
--border:    rgba(15,23,42,0.08);   /* 극도로 얇은 */
--text:      #0F172A;
--text-2:    #475569;
--accent:    #6366F1;           /* 인디고 */
--accent-2:  #EC4899;           /* 코랄 핑크 — 그라디언트 파트너 */
--gradient:  linear-gradient(135deg, #6366F1 0%, #EC4899 100%);
```

### 타이포그래피
- 본문: Pretendard Variable (한국어 최적)
- 강조 타이틀: **Fraunces** 또는 **Instrument Serif** (혼합 허용)
- 스케일: Display 56 / H1 40 / H2 30 / Body 17
- 타이트한 letter-spacing (-0.025em)

### 그림자 (중요!)
플랫하면 안 됨. 2겹 그림자로 **종이가 살짝 떠 있는 느낌**.

```css
.soft-shadow {
  box-shadow:
    0 1px 2px rgba(15,23,42,0.04),
    0 20px 40px -15px rgba(15,23,42,0.08);
}
.soft-shadow-lg {
  box-shadow:
    0 2px 4px rgba(15,23,42,0.04),
    0 30px 60px -20px rgba(99,102,241,0.15);
}
```

### 유리 표면 (Glassmorphism)
```css
.glass {
  background: rgba(255,255,255,0.65);
  backdrop-filter: blur(12px) saturate(140%);
  -webkit-backdrop-filter: blur(12px) saturate(140%);
  border: 1px solid rgba(255,255,255,0.8);
}
```

### 라운드
- 버튼: `rounded-full` (완전 라운드)
- 카드: `rounded-3xl` (24px)
- 이미지: `rounded-2xl` (16px)
- 입력: `rounded-2xl`

### 모션
- 호버: `transition-all duration-300 ease-out`
- 카드 hover: 2px 상승 + 그림자 강화
- 페이드인: `fade-up 0.6s ease`
- 제한: 동시 애니메이션 3개 이하

## Hero 템플릿 (HTML)

```html
<section class="relative overflow-hidden bg-gradient-to-b from-[#FBF9F5] to-[#F8F7F4] py-24">
  <!-- 배경 장식: 부드러운 원 blur -->
  <div aria-hidden class="absolute top-20 -left-20 w-96 h-96 rounded-full bg-indigo-200/30 blur-3xl"></div>
  <div aria-hidden class="absolute bottom-0 right-0 w-96 h-96 rounded-full bg-pink-200/30 blur-3xl"></div>

  <div class="max-w-6xl mx-auto px-6 relative">
    <!-- 상단 배지 -->
    <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full glass text-sm text-slate-600">
      <span class="w-2 h-2 rounded-full bg-indigo-500 animate-pulse"></span>
      2026학년도 신입생 모집 중
    </div>

    <!-- 타이틀 (세리프 혼합) -->
    <h1 class="mt-8 text-6xl font-bold tracking-korean-tight leading-[1.1]">
      학생의 <span class="italic font-serif text-indigo-600">속도</span>에 맞춰<br/>
      함께 자라는 학교
    </h1>

    <p class="mt-6 text-xl text-slate-600 max-w-2xl leading-relaxed">
      서두르지 않아도 괜찮아요. 한 명 한 명의 발걸음을 지켜보며 걸어가는,
      우리 학교의 수업 이야기를 소개합니다.
    </p>

    <!-- CTA -->
    <div class="mt-10 flex gap-4">
      <button class="px-8 py-4 rounded-full bg-gradient-to-r from-indigo-600 to-pink-500
                     text-white font-semibold shadow-lg shadow-indigo-500/30
                     hover:-translate-y-0.5 transition-all duration-300">
        입학 안내 보기
      </button>
      <button class="px-8 py-4 rounded-full glass font-semibold text-slate-800
                     hover:bg-white transition-all duration-300">
        학교 소개 영상
      </button>
    </div>
  </div>
</section>
```

## Do / Don't

✅ **Do**
- 여백을 아낌없이 (섹션 간 120px+)
- 텍스트만으로도 충분한 정보 전달
- 그라디언트는 매우 미묘하게
- 유리 효과는 배경 이미지 위에서 빛난다

❌ **Don't**
- 강한 원색(순수 #FF0000 등) 금지
- 하드 엣지 그림자 (`0 10px 20px #000`) 금지
- 빽빽한 그리드 (4열 이상) 금지
- 3개 이상의 강조색 섞지 않기

## DIALS 권장값

```text
DIALS: VARIANCE=6, MOTION=5, DENSITY=3
```

## 참고

원본: [Leonxlnx/taste-skill — soft-skill](https://github.com/Leonxlnx/taste-skill)
