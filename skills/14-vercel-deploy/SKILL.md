---
name: vercel-deploy
description: GitHub 저장소를 Vercel로 배포하는 교사 맞춤 가이드. 단일 HTML · Vite · Next.js 세 가지 시나리오 모두 커버. 커스텀 도메인·환경변수·배포 실패 대응까지.
source: 씨마스에듀 4회차 연수 오리지널
language: ko
---

# 14. vercel-deploy — GitHub → Vercel 배포 가이드

## 왜 Vercel인가

- ✅ **무료** (취미·교육용 Hobby 플랜)
- ✅ **GitHub 연동 자동 배포** — push 하면 자동으로 URL 갱신
- ✅ **HTTPS 자동** — `https://my-class-3-4.vercel.app` 처럼 안전한 URL 즉시 제공
- ✅ **빠른 CDN** — 전 세계 어디서나 빠른 로딩
- ✅ **도메인 구매 불필요** — `.vercel.app` 서브도메인 무료 제공

## 3가지 배포 시나리오

### 시나리오 A. 단일 HTML (Stitch 결과물 직접 배포) ⭐ 연수 권장

Stitch가 만든 `index.html` 하나만 있으면 바로 배포.

**1. GitHub 준비**
```bash
cd my-class-site
git init
git add .
git commit -m "학급 홍보 페이지 초안"
gh repo create my-class-site --public --source=. --push
# 또는: GitHub 웹에서 repo 만들고 → git remote add origin → push
```

**2. Vercel 연결**
- https://vercel.com 접속 → GitHub 로그인
- **Add New → Project** → 방금 만든 repo 선택
- **Framework Preset**: **Other** (HTML만이면 자동 감지)
- **Root Directory**: `./` (기본)
- **Build Command**: 비워두기
- **Output Directory**: 비워두기 (또는 `./`)
- **Deploy** 클릭 — 끝!

**3. URL 확인**
```
https://my-class-site-xyz.vercel.app
```
이 URL을 학부모·학생에게 공유.

### 시나리오 B. Vite + React

**vercel.json 불필요** — Vercel이 자동 감지. 단, 최적화하려면:

```json
{
  "$schema": "https://openapi.vercel.sh/vercel.json",
  "framework": "vite",
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "devCommand": "npm run dev",
  "installCommand": "npm install",
  "rewrites": [
    { "source": "/(.*)", "destination": "/" }
  ]
}
```

`rewrites` 는 SPA 라우팅에 필요 (React Router 쓸 때 새로고침 시 404 방지).

### 시나리오 C. Next.js

설정 없음. Vercel은 Next.js를 **완벽 자동 지원**. 그냥 push 하면 끝.

환경 변수가 필요하다면:
- Vercel 대시보드 → Project → **Settings → Environment Variables**
- `GEMINI_API_KEY=...` 같은 비밀 키 등록
- 코드에서 `process.env.GEMINI_API_KEY` 로 접근

## 자주 마주하는 배포 실패 & 해결

### ❌ 실패 1: "Build failed — Cannot find module 'tailwindcss'"
→ `package.json` 에 `tailwindcss`, `postcss`, `autoprefixer` 가 `devDependencies`에 있는지 확인. Vercel은 기본적으로 devDeps도 설치하므로, 누락이면 추가.

### ❌ 실패 2: "404 Not Found" on subpages (Vite/React)
→ `vercel.json` 에 SPA rewrites 추가 (위 시나리오 B 참고).

### ❌ 실패 3: 이미지가 안 보임
→ 경로가 `/images/hero.png` 절대경로인지 확인. 상대경로(`./images/...`)는 배포 시 깨지기 쉬움. `public/` 폴더에 넣고 `/` 시작 경로 사용.

### ❌ 실패 4: 한글 폰트가 이상함
→ Pretendard CDN 링크를 `<head>` 에 넣고, `<html lang="ko">` 로 설정. 시스템 폰트 의존 금지.

### ❌ 실패 5: 모바일에서만 레이아웃 깨짐
→ `<meta name="viewport" content="width=device-width, initial-scale=1.0">` 누락 가능성. 체크.

## 커스텀 도메인 연결 (선택)

`mysum-class.com` 같은 도메인이 있다면:

1. Vercel → Project → **Settings → Domains** → 도메인 입력
2. 도메인 제공사에서 DNS 레코드 추가:
   - A 레코드 `76.76.21.21`
   - 또는 CNAME `cname.vercel-dns.com`
3. 10분~24시간 후 SSL 자동 발급 완료

## 자동 배포 흐름 (GitHub → Vercel)

```
[코드 수정]
    ↓
[git commit + push]
    ↓
[Vercel이 webhook 감지]
    ↓
[빌드 & 배포 자동 시작]
    ↓
[1–3분 후 URL 갱신]
    ↓
[PR 마다 Preview URL 생성] ← 동료 교사에게 미리 보여주기 좋음
```

## 연수 4회차 실습 체크리스트

- [ ] GitHub 계정 로그인 완료
- [ ] Vercel 계정(= GitHub 계정) 로그인 완료
- [ ] Stitch로 만든 `index.html` 파일 준비
- [ ] 로컬 폴더에 `index.html` 저장
- [ ] GitHub Desktop 또는 웹으로 repo 생성
- [ ] Vercel 대시보드에서 Import → Deploy
- [ ] 생성된 `.vercel.app` URL 접속 확인
- [ ] 모바일(휴대폰)에서도 열어 확인
- [ ] 단톡방에 URL 공유

## Vercel CLI (고급)

터미널에서 직접 배포:

```bash
npm i -g vercel
vercel login
vercel               # 현재 폴더 배포 (프리뷰)
vercel --prod        # 프로덕션 배포
vercel env add       # 환경 변수 추가
vercel logs          # 배포 로그 확인
```

## 대안 플랫폼

Vercel 외에도 비슷한 서비스:

- **Netlify** — 거의 동일, 폼 처리 기능이 조금 더 친절
- **Cloudflare Pages** — 더 빠른 글로벌 CDN, 무료 bandwidth 무제한
- **GitHub Pages** — 완전 무료, 정적 파일만 (빌드 불가)

4회차 연수에서는 **Vercel**을 표준으로 사용합니다.

## 참고

- [Vercel 공식 문서](https://vercel.com/docs)
- [Vercel 무료 플랜 한도](https://vercel.com/docs/limits)
- [한국어 한글 도메인 등록 가이드](https://vercel.com/docs/projects/domains/add-a-domain)
