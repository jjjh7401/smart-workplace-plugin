---
name: workplace-ai-image-prompt
description: |
  AI 이미지 생성 프롬프트 스킬. 비즈니스 목적에 맞는 Midjourney, Stable Diffusion, DALL-E 프롬프트를 설계합니다.
  Use when creating AI image prompts, Midjourney, Stable Diffusion, AI 이미지 프롬프트, 이미지 생성.
allowed-tools: Read, Write, Edit
user-invocable: true
version: 1.0.0
status: active
---

# AI 이미지 생성 프롬프트 가이드

## 빠른 참조 (Quick Reference)

### 플랫폼별 특성
| 플랫폼 | 강점 | 약점 | 권장 용도 |
|--------|------|------|-----------|
| Midjourney | 예술적/감성적 | 텍스트 렌더링 약함 | 마케팅, 브랜딩 |
| DALL-E 3 | 텍스트 이해력 | 일관성 유지 어려움 | 빠른 프로토타입 |
| Stable Diffusion | 커스터마이징 | 설치/설정 필요 | 대량 생성, 일관성 |
| Adobe Firefly | 상업 라이선스 | 스타일 제한적 | 상업용 안전 이미지 |

### 프롬프트 기본 공식
```
[주제/인물] + [스타일/분위기] + [구도] + [조명] + [색감] + [기술적 설정]
```

---

## 비즈니스 목적별 프롬프트

### 1. 기업 마케팅 이미지

#### 제품 홍보 이미지 (Midjourney)
```
/imagine professional product photography of [제품명],
clean white studio background, soft natural lighting,
high-end commercial photography style,
sharp focus, 8k ultra-detailed,
minimalist Korean aesthetic --ar 1:1 --v 6

한국어 설명:
[제품명]의 전문 제품 사진, 깔끔한 흰색 스튜디오 배경,
부드러운 자연 조명, 고급 상업 사진 스타일, 선명한 포커스
```

#### 브랜드 SNS 이미지
```
/imagine Korean office workspace aesthetic,
modern minimalist desk setup, [브랜드 컬러] accents,
natural light through windows, lifestyle photography,
warm professional atmosphere, editorial style,
--ar 4:5 --v 6 --stylize 150

한국어 설명:
한국 오피스 작업공간 미학, 현대적 미니멀 데스크,
[브랜드 컬러] 포인트, 창문 통한 자연광, 라이프스타일 사진
```

### 2. 프레젠테이션용 이미지

#### 배경 이미지
```
/imagine abstract business background,
[색상1] to [색상2] gradient, geometric shapes,
professional corporate design, clean minimal,
no text, suitable for presentation slide background,
--ar 16:9 --v 6

예시:
deep navy blue to royal blue gradient,
subtle geometric mesh pattern, corporate professional,
--ar 16:9 --v 6
```

#### 개념 설명 이미지
```
/imagine isometric illustration of [비즈니스 개념],
flat design style, Korean corporate aesthetic,
[주요 색상] color scheme, icon-style elements,
clean vector look, white background,
--ar 16:9 --v 6

예시 (디지털 트랜스포메이션):
isometric illustration of digital transformation,
connecting traditional office to cloud technology,
flat design, blue and white color scheme
```

### 3. 인물 사진 (인물 생성 시 주의 필요)

#### 비즈니스 일러스트레이션 (인물 포함)
```
/imagine diverse Korean business team meeting,
modern conference room, professional attire,
warm collaborative atmosphere, diversity included,
editorial photography style, natural candid feel,
--ar 16:9 --v 6

※ 실제 특정인 묘사 금지, 일반적 직장인 이미지로 생성
```

### 4. 블로그/SNS 썸네일

#### 정보성 콘텐츠 썸네일
```
/imagine eye-catching thumbnail background for Korean blog post,
topic: [주제], vibrant colors [색상 팔레트],
dynamic composition, bold graphic elements,
no text in image, suitable for text overlay,
--ar 16:9 --v 6

예: topic: Excel tips and tricks,
blue and yellow vibrant colors, spreadsheet elements,
modern flat illustration style
```

---

## Stable Diffusion 프롬프트

### 기본 구조
```
Positive prompt:
[내용 설명], [스타일], [품질 태그]
masterpiece, best quality, highly detailed,
professional photography, 8k

Negative prompt:
ugly, blurry, low quality, watermark, text,
deformed, bad anatomy, poorly drawn
```

### 비즈니스 스타일 예시
```
Positive:
professional Korean business woman, 30s, confident smile,
modern office background, business casual attire,
natural lighting, editorial photography,
masterpiece, best quality, photorealistic

Negative:
cartoon, anime, unrealistic, distorted features,
low quality, blurry, watermark
```

---

## DALL-E 3 프롬프트 (ChatGPT/API)

### 텍스트 포함 이미지 생성 강점 활용
```
"[언어]로 텍스트가 포함된 [이미지 유형] 생성:
메인 텍스트: '[텍스트 내용]'
스타일: [스타일]
배경: [배경 설명]
색상: [색상 팔레트]"

예:
"한국어로 텍스트가 포함된 인포그래픽 카드 생성:
메인 텍스트: '매출 23% 성장'
스타일: 현대적 비즈니스 카드, 미니멀
배경: 깔끔한 흰색 배경
색상: 네이비 블루 (#1B4F9E)와 흰색"
```

---

## 구현 가이드

### 프롬프트 작성 7단계
1. **목적 정의**: 어디에 쓸 이미지인가?
2. **스타일 선택**: 사실적/일러스트/추상 중 선택
3. **구도 결정**: 비율(16:9, 1:1, 4:5) 설정
4. **핵심 요소 나열**: 반드시 포함될 것들
5. **분위기 키워드**: 전달하고 싶은 감성
6. **품질 태그 추가**: 플랫폼별 품질 향상 태그
7. **반복 생성 및 선택**: 4-8장 생성 후 최선 선택

### 저작권 및 상업 사용 주의
```
안전한 상업 사용:
✅ Adobe Firefly: 상업 라이선스 포함
✅ DALL-E 3: OpenAI 이용약관 확인 필요
✅ Midjourney Pro: 상업 사용 가능
⚠️  Midjourney Free: 비상업용만

유명인/브랜드 절대 금지:
- 실존 인물 묘사 금지
- 타 브랜드 로고/제품 포함 금지
```

---

## 고급 패턴

### 브랜드 일관성 유지
```
시드(Seed) 번호 활용 (Midjourney):
--seed [숫자] 로 같은 스타일 유지

스타일 레퍼런스:
--sref [이미지URL] 로 특정 스타일 참조

캐릭터 일관성:
--cref [이미지URL] 로 같은 캐릭터 유지
```

### 다국어 프롬프트 전략
```
영어 프롬프트 > 한국어 프롬프트 (품질 차이 있음)
한국적 요소 표현 시:
- "Korean aesthetic" 명시
- "hanbok", "Korean traditional" 등 구체 키워드
- "K-style", "Seoul urban" 등 현대적 키워드
```

---

## 관련 스킬

- workplace-sns-content: 생성된 이미지를 활용한 SNS 콘텐츠 작성
- workplace-ppt-design: PPT 배경 및 삽화 이미지 생성
- workplace-svg-infographic: AI 이미지 대신 SVG로 인포그래픽 제작
