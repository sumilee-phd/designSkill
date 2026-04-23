---
name: remotion-video
description: 완성된 Stitch 사이트·앱의 홍보 영상을 Remotion으로 자동 생성. 부드러운 전환·줌·텍스트 오버레이로 1–2분 짜리 소개 영상 제작.
source: google-labs-code/stitch-skills
language: ko
---

# 12. remotion-video — 앱 소개 영상 자동 제작

## Remotion이란

React 코드로 **프로그래머블 영상**을 만드는 프레임워크. 모션그래픽·화면 녹화·애니메이션을 **코드로 정의**해 MP4로 렌더.

## 언제 사용하나

- 완성된 교실 앱을 **부모님·동료 교사에게 공유**할 영상이 필요할 때
- 학교 행사 홍보 릴스·쇼츠 (9:16)
- 연수 결과물을 **연수 채널에 업로드**할 때
- 홈페이지 Hero에 **자동재생 배경 영상**이 필요할 때

## 설치

```bash
npx create-video@latest my-class-intro
cd my-class-intro
npm install
npm start   # Remotion Studio 열림
```

## 자동 생성되는 영상 구조 (60초 템플릿)

```
0:00 – 0:03  인트로: 학급 로고 · "4학년 3반"
0:03 – 0:10  Hero 캡처 · 페이드 줌인
0:10 – 0:25  핵심 기능 3개 (각 5초, 카드별 슬라이드)
0:25 – 0:40  학생 작품 갤러리 (자동 스크롤)
0:40 – 0:55  담임 메시지 · 실제 페이지 URL
0:55 – 1:00  아웃트로: QR 코드 + "함께해요"
```

## 교실 앱용 Remotion Composition 예시

```tsx
// src/compositions/ClassIntro.tsx
import { Composition, AbsoluteFill, Sequence, useCurrentFrame, interpolate } from 'remotion';
import { Img, spring, useVideoConfig } from 'remotion';

export const ClassIntro: React.FC<{ className: string; heroImage: string }> = ({
  className, heroImage,
}) => {
  const frame = useCurrentFrame();
  const { fps, durationInFrames } = useVideoConfig();

  return (
    <AbsoluteFill style={{ backgroundColor: '#FFF8F0' }}>

      {/* 0~3초 인트로 */}
      <Sequence from={0} durationInFrames={fps * 3}>
        <Intro className={className} />
      </Sequence>

      {/* 3~10초 Hero 줌인 */}
      <Sequence from={fps * 3} durationInFrames={fps * 7}>
        <HeroZoom src={heroImage} />
      </Sequence>

      {/* 10~25초 기능 3개 */}
      <Sequence from={fps * 10} durationInFrames={fps * 15}>
        <Features />
      </Sequence>

      {/* ... */}
    </AbsoluteFill>
  );
};

const Intro: React.FC<{ className: string }> = ({ className }) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  const scale = spring({ frame, fps, config: { damping: 12 } });

  return (
    <AbsoluteFill style={{ justifyContent: 'center', alignItems: 'center' }}>
      <div style={{
        transform: `scale(${scale})`,
        fontFamily: 'Pretendard Variable',
        fontSize: 120,
        fontWeight: 800,
        letterSpacing: '-0.025em',
        color: '#FF8A65',
      }}>
        {className} 🌱
      </div>
    </AbsoluteFill>
  );
};

// Root.tsx
export const RemotionRoot: React.FC = () => (
  <Composition
    id="ClassIntro"
    component={ClassIntro}
    durationInFrames={60 * 30}  // 60초 @ 30fps
    fps={30}
    width={1920}
    height={1080}
    defaultProps={{ className: '4학년 3반', heroImage: '/hero.png' }}
  />
);
```

## 렌더링

```bash
# 영상 파일로 렌더
npx remotion render ClassIntro out/class-intro.mp4

# 세로(9:16) 쇼츠 버전
npx remotion render ClassIntro out/short.mp4 --props '{"aspect":"9:16"}'

# GIF 로 (프리뷰용)
npx remotion render ClassIntro out/preview.gif --codec=gif --fps=15
```

## 한국어 자막 가이드

한국어는 영어보다 **글자 수 기준 체류 시간이 짧음**. 자막 한 줄 규칙:

- 1행 **18자 이하** (가로 영상), **12자 이하** (세로 쇼츠)
- 한 번에 2행 이내
- 화면에 최소 **2.5초** 유지
- 줄바꿈은 문장 의미 단위 (조사 앞 끊지 말 것)

```tsx
const Subtitle: React.FC<{ text: string; from: number }> = ({ text, from }) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();
  const localFrame = frame - from;
  const opacity = interpolate(localFrame, [0, 10, 60, 70], [0, 1, 1, 0], {
    extrapolateRight: 'clamp',
  });

  return (
    <div style={{
      position: 'absolute', bottom: 80, width: '100%', textAlign: 'center',
      fontFamily: 'Pretendard Variable', fontWeight: 700, fontSize: 42,
      color: 'white', textShadow: '0 2px 8px rgba(0,0,0,0.5)',
      letterSpacing: '-0.025em', wordBreak: 'keep-all',
      opacity,
    }}>
      {text}
    </div>
  );
};
```

## 사용 방법

```text
@skills/12-remotion-video 로 다음 사이트의 60초 홍보 영상 만들어줘:
- URL: https://class-4-3.vercel.app
- 분위기: 따뜻한 파스텔
- 자막: 한국어 (학부모 타겟)
- 비율: 9:16 (인스타 쇼츠용)
```

## 참고

원본: [google-labs-code/stitch-skills/remotion](https://github.com/google-labs-code/stitch-skills/tree/main/skills/remotion)
공식: [Remotion](https://www.remotion.dev/)
