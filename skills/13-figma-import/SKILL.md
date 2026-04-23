---
name: figma-import
description: Figma 디자인 URL 하나로 프로덕션 코드를 자동 생성. Figma MCP 서버 기반, get_design_context + get_screenshot으로 픽셀 퍼펙트 구현. (선택 스킬 — MCP 필요)
source: openai/skills (figma-implement-design)
language: ko
---

# 13. figma-import — Figma → 코드 (선택)

⚠️ **주의**: 이 스킬은 **Figma MCP 서버 연동**이 필요합니다. Figma 사용 경험이 없다면 스킬 01–12만 사용해도 연수 수업에 충분합니다.

## 언제 사용하나

- **동료 교사나 디자인 전공 선생님**이 Figma로 만든 시안을 코드로 옮겨야 할 때
- 학교 신규 브랜딩을 Figma로 받았고, 홈페이지 리뉴얼에 반영할 때
- 학생들이 Figma로 작업한 포트폴리오를 **실제 웹 앱으로 배포**할 때

## 사전 준비

### 1. Figma MCP 서버 설치
```bash
# Claude Code 사용자
# 설정 파일에 추가
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-figma"],
      "env": { "FIGMA_ACCESS_TOKEN": "figd_..." }
    }
  }
}
```

### 2. Figma Personal Access Token 발급
Figma → Account Settings → Personal Access Tokens → Create

### 3. 대상 파일 URL 확인
```
https://figma.com/design/{fileKey}/{fileName}?node-id={nodeId}
```

## 변환 파이프라인

### ① `get_design_context` — 구조 추출
Figma API로 선택된 노드의 **논리 구조** 추출:

```json
{
  "name": "HeroSection",
  "type": "FRAME",
  "layout": { "mode": "VERTICAL", "gap": 24, "padding": 48 },
  "typography": [
    { "role": "heading", "fontFamily": "Pretendard", "fontSize": 48, "weight": 700 }
  ],
  "colors": { "background": "#FFF8F0", "text": "#1F2937" },
  "components": [
    { "name": "Button/Primary", "props": { "label": "학급 소식 보기" } }
  ],
  "spacing": { "sectionGap": 120 }
}
```

### ② `get_screenshot` — 비주얼 정답
동일 노드의 **실제 렌더링 이미지** 다운로드 → AI가 코드 결과물과 **비교 검증**.

### ③ 코드 생성 (React + Tailwind)
위 두 정보를 조합해 React 컴포넌트 생성. 기본 출력:

```tsx
export const HeroSection = () => (
  <section className="flex flex-col gap-6 px-12 py-16 bg-[#FFF8F0]">
    <h1 className="text-5xl font-bold text-slate-900 tracking-korean-tight">
      학급 소식을 한눈에
    </h1>
    <Button variant="primary">학급 소식 보기</Button>
  </section>
);
```

### ④ 시각 검증
생성 코드를 Playwright로 스크린샷 → 원본과 **픽셀 diff** 자동 리포트:

```
✓ HeroSection: 99.2% 일치
⚠ 제목 line-height가 원본보다 2px 넓음 → tracking-tight 추가 권장
```

## 교사·학생 시나리오

### 시나리오: 학생 포트폴리오 Figma → Vercel 배포

1. 학생이 Figma로 포트폴리오 시안 제출
2. 교사가 `@skills/13-figma-import` 로 React 프로젝트 자동 생성
3. `skills/09-react-convert` 와 병행해 컴포넌트 정리
4. `skills/14-vercel-deploy` 로 배포
5. 학생에게 URL 공유 → 프로젝트 완료

## 한계 및 주의

- Figma에서 **복잡한 Variant 구조**는 100% 변환되지 않을 수 있음 → 수동 다듬기 필요
- Auto Layout이 없는 프레임은 레이아웃 추출 정확도 하락 → **Auto Layout 사용 권장**
- 한국어 폰트가 Figma에 없으면 Pretendard로 자동 대체
- 저작권 보호된 폰트·이미지는 변환 제외

## 대안: Figma 없이 시안 만들기

Figma가 없어도 **Stitch 자체**가 시안 + 코드를 동시에 생성합니다. 4회차 연수에서는 이 방법을 권장합니다 (skills 01–12 참고).

## 참고

원본: [openai/skills — figma-implement-design](https://github.com/openai/skills/blob/main/skills/.curated/figma-implement-design/SKILL.md)
Figma MCP: [Model Context Protocol Figma Server](https://github.com/modelcontextprotocol/servers)
