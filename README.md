# 슬기로운 직장생활 - Smart Workplace Plugin

한국형 직장인을 위한 종합 업무 자동화 Claude Code 플러그인입니다.
24종 스킬과 7종 슬래시 커맨드로 이메일, 보고서, 계약서, 사업계획서 등 모든 업무 문서를 즉시 처리합니다.

---

## 설치 방법

### 로컬 설치

```bash
claude plugin add ./
```

### 마켓플레이스에서 설치

```bash
claude plugin add smart-workplace
```

---

## 슬래시 커맨드 (7종)

### `/smart-workplace:daily-report` - 일일 업무 보고서

오늘의 업무 일일보고서를 즉시 작성합니다.

**사용법:**

```
/smart-workplace:daily-report
/smart-workplace:daily-report 오전에 기획서 작성 완료, 오후에 클라이언트 미팅 참석
```

**출력 항목:**
- 금일 완료 업무
- 진행 중 업무
- 익일 계획
- 특이사항

---

### `/smart-workplace:quick-email` - 비즈니스 이메일 작성

상황과 목적에 맞는 전문적인 한국 비즈니스 이메일을 즉시 생성합니다.

**사용법:**

```
/smart-workplace:quick-email
/smart-workplace:quick-email 거래처에 납품 일정 연기 요청 이메일
```

**지원 유형:**
- 미팅 요청 / 일정 조율
- 자료 요청 / 제출
- 사과 / 해명
- 감사 / 인사
- 업무 보고 / 공유

---

### `/smart-workplace:resume-check` - 이력서 및 자기소개서 검토

지원 직군에 맞는 강점을 부각하고 약점을 보완하여 합격률을 높여드립니다.

**사용법:**

```
/smart-workplace:resume-check
/smart-workplace:resume-check [이력서 전체 내용 붙여넣기]
```

**제공 내용:**
- 강점 분석
- 개선 필요 사항 (구체적 제안 포함)
- 직무적합성 평가
- 수정된 버전
- 한국 취업 시장 맞춤 조언

---

### `/smart-workplace:meeting-prep` - 회의 준비 및 회의록 템플릿

효율적인 회의를 위한 구조화된 문서를 제공합니다.

**사용법:**

```
/smart-workplace:meeting-prep
/smart-workplace:meeting-prep 2026년 1분기 마케팅 전략 수립 회의
```

**제공 내용:**
- 회의 안건 목록 (시간 배분 포함)
- 회의록 템플릿 (사전 작성)
- 사전 준비사항 체크리스트
- 결정사항 및 액션 아이템 추적표

---

### `/smart-workplace:prompt-craft` - 업무용 AI 프롬프트 설계

원하는 결과를 얻기 위한 최적화된 AI 프롬프트를 작성합니다.

**사용법:**

```
/smart-workplace:prompt-craft
/smart-workplace:prompt-craft 영업 제안서 초안 작성에 쓸 프롬프트
```

**제공 내용:**
- 최적화된 프롬프트 (한국어)
- 각 요소 설명
- 사용 방법 가이드
- 상황별 변형 옵션 2-3가지
- 주의사항

---

### `/smart-workplace:contract-check` - 계약서 위험 조항 분석

불리한 조항, 모호한 표현, 누락된 보호 조항을 파악하고 개선안을 제시합니다.

**사용법:**

```
/smart-workplace:contract-check
/smart-workplace:contract-check [계약서 전체 내용 붙여넣기]
```

**제공 내용:**
- 위험 조항 목록 (심각도: 상/중/하)
- 모호한 표현 목록
- 누락된 보호 조항
- 수정 제안
- 전반적 리스크 평가

> **주의:** AI 분석은 참고용이며, 법적 효력을 위해서는 반드시 변호사와 상담하세요.

---

### `/smart-workplace:biz-plan` - 사업계획서 초안 작성

투자자와 심사위원을 위한 전문적인 사업계획서를 생성합니다.

**사용법:**

```
/smart-workplace:biz-plan
/smart-workplace:biz-plan AI 기반 개인 맞춤형 영양 관리 앱, B2C, 구독 모델
```

**포함 항목:**
- 사업 개요 (Executive Summary)
- 시장 분석 (한국 시장 맥락 포함)
- 사업 모델 및 가치 제안
- 마케팅 전략
- 운영 계획
- 재무 계획 (3년)
- 팀 구성
- 리스크 분석

---

## 스킬 목록 (24종)

### 문서 작성 스킬 (Document Skills)

| 스킬명 | 설명 |
|--------|------|
| workplace-korean-report | 한국형 업무 보고서 작성 표준 및 서식 |
| workplace-business-email | 비즈니스 이메일 어조 및 형식 가이드 |
| workplace-meeting-minutes | 회의록 작성 표준 및 템플릿 |
| workplace-proposal-writing | 제안서 작성 구조 및 설득 전략 |
| workplace-presentation-deck | 프레젠테이션 구성 및 슬라이드 작성 |
| workplace-technical-doc | 기술 문서 작성 표준 |

### 비즈니스 전략 스킬 (Business Skills)

| 스킬명 | 설명 |
|--------|------|
| workplace-business-plan | 사업계획서 작성 표준 및 투자자 설득 기법 |
| workplace-contract-review | 한국 계약서 검토 기준 및 위험 조항 분석 |
| workplace-market-analysis | 시장 분석 방법론 및 한국 시장 특성 |
| workplace-financial-modeling | 재무 모델링 및 수익 예측 방법 |
| workplace-negotiation-tactics | 한국 비즈니스 협상 전략 |
| workplace-startup-toolkit | 스타트업 창업 실무 가이드 |

### 커리어 개발 스킬 (Career Skills)

| 스킬명 | 설명 |
|--------|------|
| workplace-portfolio-resume | 한국 이력서 및 자기소개서 작성 표준 |
| workplace-job-interview | 면접 준비 및 한국 직장 문화 이해 |
| workplace-performance-review | 성과 평가 작성 및 역량 개발 계획 |
| workplace-salary-negotiation | 연봉 협상 전략 및 시장 급여 분석 |
| workplace-linkedin-profile | LinkedIn 프로필 최적화 (한국 시장) |
| workplace-personal-branding | 개인 브랜딩 전략 |

### AI 업무 활용 스킬 (AI Productivity Skills)

| 스킬명 | 설명 |
|--------|------|
| workplace-prompt-engineering | 업무용 AI 프롬프트 설계 고급 기법 |
| workplace-data-analysis | 업무 데이터 분석 및 시각화 방법 |
| workplace-automation-workflow | 반복 업무 자동화 설계 |
| workplace-ai-ethics | 직장 내 AI 윤리적 활용 가이드 |
| workplace-productivity-system | 개인 생산성 시스템 구축 (GTD, PKM) |
| workplace-knowledge-management | 팀 지식 관리 및 문서화 전략 |

---

## 사용 에이전트 (Agents)

이 플러그인은 다음 전문 에이전트를 활용합니다:

- **workplace-document-expert**: 업무 문서 전문가 (보고서, 이메일, 회의록)
- **workplace-business-expert**: 비즈니스 전략 전문가 (계약서, 사업계획서)
- **workplace-career-expert**: 커리어 개발 전문가 (이력서, 면접, 성과관리)

---

## 시스템 요구사항

- Claude Code v2.0.0 이상
- 인터넷 연결 (AI 기능 사용 시)

---

## 작성자 및 라이선스

- **작성자**: jjjh7401
- **라이선스**: MIT
- **버전**: 1.0.0

---

## 기여 및 피드백

버그 리포트, 기능 제안, 개선 의견을 환영합니다.
이 플러그인이 여러분의 직장 생활을 조금이라도 슬기롭게 만들어드리길 바랍니다.
