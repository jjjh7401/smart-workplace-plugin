---
name: workplace-svg-infographic
description: |
  SVG 도식화 및 인포그래픽 생성 스킬. 비즈니스 프로세스, 조직도, 데이터 시각화를 SVG로 생성합니다.
  Use when creating SVG diagrams, infographics, business charts, SVG 도식화, 인포그래픽, 조직도, 프로세스 맵.
allowed-tools: Read, Write, Edit
user-invocable: true
version: 1.0.0
status: active
---

# SVG 도식화 및 인포그래픽 생성 가이드

## 빠른 참조 (Quick Reference)

### SVG 기본 요소
| 요소 | 설명 | 예시 |
|------|------|------|
| `<rect>` | 사각형 | 카드, 배경 박스 |
| `<circle>` | 원 | 숫자 표시, 아이콘 |
| `<text>` | 텍스트 | 레이블, 제목 |
| `<line>` | 선 | 연결선, 구분선 |
| `<path>` | 경로 | 화살표, 복잡한 도형 |
| `<polygon>` | 다각형 | 화살표 머리 |
| `<g>` | 그룹 | 요소 묶기 |

### 비즈니스 색상 팔레트 (SVG용)
```
네이비:   #1B4F9E   (신뢰, 전문성)
파랑:     #2E7FD9   (강조, 포인트)
연파랑:   #EBF3FD   (배경)
초록:     #16A34A   (성공, 완료)
주황:     #D97706   (진행 중, 주의)
빨강:     #E74C3C   (중요, 문제)
그레이:   #6B7280   (보조 텍스트)
밝은회색: #F5F5F5   (배경)
```

---

## SVG 템플릿 모음

### 1. 프로세스 플로우 차트
```svg
<svg width="800" height="200" xmlns="http://www.w3.org/2000/svg"
     font-family="맑은 고딕, Malgun Gothic, sans-serif">

  <!-- 단계 1 -->
  <rect x="20" y="60" width="140" height="60" rx="8"
        fill="#1B4F9E" stroke="none"/>
  <text x="90" y="86" fill="white" text-anchor="middle"
        font-size="14" font-weight="bold">① 요건 분석</text>
  <text x="90" y="106" fill="#EBF3FD" text-anchor="middle"
        font-size="11">현황 파악</text>

  <!-- 화살표 -->
  <line x1="160" y1="90" x2="195" y2="90"
        stroke="#6B7280" stroke-width="2"/>
  <polygon points="195,85 205,90 195,95"
           fill="#6B7280"/>

  <!-- 단계 2 -->
  <rect x="205" y="60" width="140" height="60" rx="8"
        fill="#2E7FD9" stroke="none"/>
  <text x="275" y="86" fill="white" text-anchor="middle"
        font-size="14" font-weight="bold">② 설계</text>
  <text x="275" y="106" fill="#EBF3FD" text-anchor="middle"
        font-size="11">솔루션 설계</text>

  <!-- 화살표 -->
  <line x1="345" y1="90" x2="380" y2="90"
        stroke="#6B7280" stroke-width="2"/>
  <polygon points="380,85 390,90 380,95"
           fill="#6B7280"/>

  <!-- 단계 3 -->
  <rect x="390" y="60" width="140" height="60" rx="8"
        fill="#16A34A" stroke="none"/>
  <text x="460" y="86" fill="white" text-anchor="middle"
        font-size="14" font-weight="bold">③ 구현</text>
  <text x="460" y="106" fill="#EBF3FD" text-anchor="middle"
        font-size="11">개발/실행</text>

  <!-- 화살표 -->
  <line x1="530" y1="90" x2="565" y2="90"
        stroke="#6B7280" stroke-width="2"/>
  <polygon points="565,85 575,90 565,95"
           fill="#6B7280"/>

  <!-- 단계 4 -->
  <rect x="575" y="60" width="140" height="60" rx="8"
        fill="#D97706" stroke="none"/>
  <text x="645" y="86" fill="white" text-anchor="middle"
        font-size="14" font-weight="bold">④ 완료</text>
  <text x="645" y="106" fill="#EBF3FD" text-anchor="middle"
        font-size="11">검토/배포</text>
</svg>
```

### 2. 조직도
```svg
<svg width="700" height="300" xmlns="http://www.w3.org/2000/svg"
     font-family="맑은 고딕, Malgun Gothic, sans-serif">

  <!-- 대표이사 -->
  <rect x="275" y="20" width="150" height="50" rx="6"
        fill="#1B4F9E"/>
  <text x="350" y="42" fill="white" text-anchor="middle"
        font-size="13" font-weight="bold">대표이사</text>
  <text x="350" y="58" fill="#EBF3FD" text-anchor="middle"
        font-size="11">홍길동</text>

  <!-- 연결선 -->
  <line x1="350" y1="70" x2="350" y2="100"
        stroke="#6B7280" stroke-width="1.5"/>
  <line x1="150" y1="100" x2="550" y2="100"
        stroke="#6B7280" stroke-width="1.5"/>

  <!-- 영업팀 -->
  <line x1="150" y1="100" x2="150" y2="120"
        stroke="#6B7280" stroke-width="1.5"/>
  <rect x="75" y="120" width="150" height="50" rx="6"
        fill="#2E7FD9"/>
  <text x="150" y="142" fill="white" text-anchor="middle"
        font-size="13" font-weight="bold">영업팀</text>
  <text x="150" y="158" fill="#EBF3FD" text-anchor="middle"
        font-size="11">팀장: 김팀장</text>

  <!-- 개발팀 -->
  <line x1="350" y1="100" x2="350" y2="120"
        stroke="#6B7280" stroke-width="1.5"/>
  <rect x="275" y="120" width="150" height="50" rx="6"
        fill="#2E7FD9"/>
  <text x="350" y="142" fill="white" text-anchor="middle"
        font-size="13" font-weight="bold">개발팀</text>
  <text x="350" y="158" fill="#EBF3FD" text-anchor="middle"
        font-size="11">팀장: 이팀장</text>

  <!-- 마케팅팀 -->
  <line x1="550" y1="100" x2="550" y2="120"
        stroke="#6B7280" stroke-width="1.5"/>
  <rect x="475" y="120" width="150" height="50" rx="6"
        fill="#2E7FD9"/>
  <text x="550" y="142" fill="white" text-anchor="middle"
        font-size="13" font-weight="bold">마케팅팀</text>
  <text x="550" y="158" fill="#EBF3FD" text-anchor="middle"
        font-size="11">팀장: 박팀장</text>
</svg>
```

### 3. 데이터 비교 인포그래픽 (막대 차트)
```svg
<svg width="600" height="320" xmlns="http://www.w3.org/2000/svg"
     font-family="맑은 고딕, Malgun Gothic, sans-serif">

  <!-- 제목 -->
  <text x="300" y="30" text-anchor="middle"
        font-size="16" font-weight="bold" fill="#2C2C2C">
    분기별 매출 현황 (억 원)
  </text>

  <!-- Y축 -->
  <line x1="80" y1="50" x2="80" y2="260"
        stroke="#6B7280" stroke-width="1"/>
  <!-- X축 -->
  <line x1="80" y1="260" x2="560" y2="260"
        stroke="#6B7280" stroke-width="1"/>

  <!-- 막대: Q1 -->
  <rect x="110" y="160" width="80" height="100" rx="4"
        fill="#1B4F9E"/>
  <text x="150" y="155" text-anchor="middle"
        font-size="13" font-weight="bold" fill="#1B4F9E">12억</text>
  <text x="150" y="278" text-anchor="middle"
        font-size="12" fill="#6B7280">Q1</text>

  <!-- 막대: Q2 -->
  <rect x="230" y="130" width="80" height="130" rx="4"
        fill="#2E7FD9"/>
  <text x="270" y="125" text-anchor="middle"
        font-size="13" font-weight="bold" fill="#2E7FD9">15억</text>
  <text x="270" y="278" text-anchor="middle"
        font-size="12" fill="#6B7280">Q2</text>

  <!-- 막대: Q3 -->
  <rect x="350" y="110" width="80" height="150" rx="4"
        fill="#16A34A"/>
  <text x="390" y="105" text-anchor="middle"
        font-size="13" font-weight="bold" fill="#16A34A">18억</text>
  <text x="390" y="278" text-anchor="middle"
        font-size="12" fill="#6B7280">Q3</text>

  <!-- 막대: Q4 -->
  <rect x="470" y="90" width="80" height="170" rx="4"
        fill="#D97706"/>
  <text x="510" y="85" text-anchor="middle"
        font-size="13" font-weight="bold" fill="#D97706">21억</text>
  <text x="510" y="278" text-anchor="middle"
        font-size="12" fill="#6B7280">Q4</text>
</svg>
```

---

## 구현 가이드

### SVG 인포그래픽 제작 순서
1. **목적 정의**: 무엇을 전달할 것인가?
2. **데이터 수집**: 표현할 수치/관계/흐름 정리
3. **유형 선택**: 프로세스/조직도/차트/비교 중 선택
4. **레이아웃 설계**: 가로/세로 비율, 요소 배치
5. **SVG 코드 작성**: 좌표 계산하며 제작
6. **테스트**: 브라우저에서 미리보기 확인

### 좌표 계산 팁
```
viewBox="0 0 width height" 사용 시:
- 전체 너비/높이 먼저 결정
- 여백: 상하좌우 20-40px
- 요소 간격: 최소 10px
- 텍스트: text-anchor="middle" 로 중앙 정렬
```

### 한글 폰트 설정
```svg
font-family="맑은 고딕, Malgun Gothic, 나눔고딕, NanumGothic, sans-serif"
```

---

## 고급 패턴

### 애니메이션 SVG (로딩/강조)
```svg
<rect x="50" y="50" width="100" height="30" fill="#2E7FD9">
  <animate attributeName="opacity"
           values="1;0.3;1" dur="2s" repeatCount="indefinite"/>
</rect>
```

### 반응형 SVG
```svg
<!-- viewBox 사용으로 자동 크기 조정 -->
<svg viewBox="0 0 800 400"
     width="100%" height="auto"
     xmlns="http://www.w3.org/2000/svg">
```

### 타임라인 인포그래픽
```svg
<!-- 가로 타임라인 구조 -->
<line x1="50" y1="150" x2="750" y2="150"
      stroke="#1B4F9E" stroke-width="3"/>
<!-- 각 이벤트: circle + text 조합 -->
<circle cx="150" cy="150" r="12" fill="#1B4F9E"/>
<text x="150" y="135" text-anchor="middle"
      font-size="11" fill="#6B7280">2023.01</text>
<text x="150" y="175" text-anchor="middle"
      font-size="12" fill="#2C2C2C" font-weight="bold">런칭</text>
```

---

## 관련 스킬

- workplace-ppt-design: SVG 이미지를 PPT에 삽입하는 디자인 시스템
- workplace-data-report: 데이터를 SVG 차트로 시각화
- workplace-sns-content: SNS용 인포그래픽 SVG 제작
