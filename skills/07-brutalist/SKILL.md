---
name: brutalist
description: 실험적이고 기계적인 Swiss 타이포그래피 브루탈리즘. 하드 엣지·거대 타이포·강한 대비로 독특한 개성 표현.
source: Leonxlnx/taste-skill
language: ko
---

# 07. brutalist — 실험적 브루탈리즘

## 분위기

- **느낌**: Gumroad · Are.na · 독립 매거진 · 90년대 웹 감성 + 현대 Swiss
- **키워드**: 날것 · 노이즈 · 모노스페이스 · 직사각형 · 강한 대비
- **적합 맥락**: 동아리 포스터·축제 티저·전시회·고등학생 창작물·풍자/시사 과제

⚠️ **주의**: 학부모·공식 문서에는 **절대 사용 금지**. 학생 개성 표현·예술 창작 맥락 한정.

## 핵심 규칙

### 색
```css
--bg:       #F0EEE6;           /* 뉴스프린트 베이지 */
--bg-alt:   #000000;           /* 검정 섹션 */
--text:     #000000;
--text-inv: #FFFFFF;
--accent:   #FF3B00;           /* 형광 주황 */
--accent-2: #00FF85;           /* 형광 그린 (경고음 느낌) */
--accent-3: #FFFF00;           /* 형광 옐로우 */
```

### 타이포그래피
- 헤딩: **IBM Plex Mono** / **Space Mono** / **Pretendard Black** — 모노스페이스 중심
- 본문: Pretendard Variable
- **극단적 크기 대비**: 제목 120px · 본문 14px
- letter-spacing: tight + UPPERCASE
- 단어를 **의도적으로 줄바꿈** 해서 타이포 자체를 그래픽으로

### 레이아웃
- 하드 그리드 (12단 표시)
- 테두리 `border-2 border-black` 또는 `border-4`
- 라운드 **완전 금지** (`rounded-none`)
- 그림자 **완전 금지** — 대신 `offset shadow` (아래 설명)

### 오프셋 섀도우
```css
.brutalist-shadow {
  box-shadow: 8px 8px 0 0 #000000; /* 검은 블록 그림자 */
}
.brutalist-shadow-color {
  box-shadow: 8px 8px 0 0 #FF3B00; /* 형광색 버전 */
}
```

## Hero 템플릿

```html
<section class="min-h-screen bg-[#F0EEE6] border-b-4 border-black">
  <!-- 상단 바: 뉴스 헤더 느낌 -->
  <div class="border-b-2 border-black px-6 py-2 flex justify-between text-xs font-mono uppercase">
    <span>VOL. 24 · ISSUE 05</span>
    <span>2026.05.21 · KR</span>
    <span>UPPER HANGANG SCHOOL</span>
  </div>

  <div class="px-8 py-16">
    <!-- 거대 타이포 -->
    <h1 class="font-mono font-black uppercase leading-[0.9] tracking-tight"
        style="font-size: clamp(60px, 12vw, 180px);">
      ART<br/>
      <span class="text-[#FF3B00]">FESTIVAL</span><br/>
      2026
    </h1>

    <!-- 한국어 서브 -->
    <p class="mt-8 text-lg max-w-md font-mono leading-relaxed">
      5.28 금 / 체육관 / 18:00<br/>
      전교생 창작 작품 · 무료 관람<br/>
      입장 제한 없음.
    </p>

    <!-- CTA: 검은 박스 -->
    <button class="mt-10 inline-block bg-black text-white font-mono font-bold
                   uppercase px-8 py-4 text-xl border-2 border-black
                   hover:bg-[#FF3B00] hover:border-[#FF3B00]
                   transition-colors duration-150"
            style="box-shadow: 6px 6px 0 0 #FF3B00;">
      → 작품 신청
    </button>
  </div>

  <!-- 하단 티커 (무한 스크롤) -->
  <div class="border-t-2 border-black bg-black text-[#00FF85] font-mono py-2 overflow-hidden">
    <div class="animate-marquee whitespace-nowrap">
      ★ 한강예술고 제24회 예술제 ★ 회화 · 조소 · 미디어 · 퍼포먼스 ★ 전시 5.28–6.03 ★
      ★ 한강예술고 제24회 예술제 ★ 회화 · 조소 · 미디어 · 퍼포먼스 ★ 전시 5.28–6.03 ★
    </div>
  </div>
</section>
```

## 대표 패턴

### 텍스트 블록 (강조)
```html
<div class="border-2 border-black bg-yellow-300 p-6">
  <h3 class="font-mono font-bold uppercase text-2xl">NOTICE.</h3>
  <p class="mt-2 font-mono">전시 기간 중 체육관 1층 출입구만 사용.</p>
</div>
```

### 테이블 (엑셀 같은 느낌)
```html
<table class="w-full font-mono border-2 border-black">
  <thead class="bg-black text-white">
    <tr>
      <th class="border-r-2 border-white p-3 text-left">DATE</th>
      <th class="border-r-2 border-white p-3 text-left">EVENT</th>
      <th class="p-3 text-left">LOCATION</th>
    </tr>
  </thead>
  <tbody>
    <tr class="border-b-2 border-black">
      <td class="border-r-2 border-black p-3">05.28</td>
      <td class="border-r-2 border-black p-3">OPENING</td>
      <td class="p-3">GYM 1F</td>
    </tr>
  </tbody>
</table>
```

## Do / Don't

✅ **Do**
- 모든 텍스트는 UPPERCASE (한국어는 볼드 대체)
- 섹션 경계는 2px 검은 선
- 형광색은 **딱 1–2개만** 포인트로
- 의도적 가독성 저하 (예술 의도)

❌ **Don't**
- 라운드·그라디언트·부드러운 그림자 금지
- 학부모 공식 문서에 사용 금지
- 유치한 이모지 남발 금지 (대신 ★ ▲ → 등 기호)

## DIALS 권장값

```text
DIALS: VARIANCE=9, MOTION=7, DENSITY=6
```

## 참고

원본: [Leonxlnx/taste-skill — brutalist-skill](https://github.com/Leonxlnx/taste-skill)
