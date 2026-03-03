---
name: workplace-business-translation
description: |
  비즈니스 한영/영한 번역 스킬. 이메일, 계약서, 보고서 등 업무 문서의 전문적인 한영 번역을 지원합니다.
  Use when translating Korean-English business documents, 번역, 한영 번역, 영한 번역, business translation.
allowed-tools: Read, Write, Edit
user-invocable: true
version: 1.0.0
status: active
---

# 비즈니스 한영/영한 번역 가이드

## 빠른 참조 (Quick Reference)

### 번역 유형별 특성
| 유형 | 핵심 원칙 | 주의사항 |
|------|-----------|----------|
| 이메일 | 경어 수준 적절히 변환 | 호칭 처리 |
| 계약서 | 법률 용어 정확성 최우선 | 오역 시 법적 문제 |
| 보고서 | 명확성, 일관된 용어 | 숫자/단위 확인 |
| 마케팅 | 자연스러운 현지화 | 문화적 맥락 |
| 기술 문서 | 전문 용어 통일 | 용어집 활용 |

### 한국어 경어 → 영어 변환 원칙
```
한국어 경어 수준은 영어에서 공식성(Formality)으로 표현
- 최고 격식 (격식체): Formal, 조동사 would/could
- 일반 격식 (일반체): Semi-formal
- 비격식 (반말): Informal, Direct

경어 번역:
- "~해주시면 감사하겠습니다" → "I would appreciate it if you could ~"
- "~부탁드립니다" → "I kindly request ~" / "Please ~"
- "~드립니다" → "I would like to inform you ~"
```

---

## 비즈니스 이메일 번역

### 한→영 이메일 번역 패턴

#### 인사말 번역
```
한국어 → 영어

"안녕하세요, 홍길동입니다."
→ "Dear [Title] [Last Name]," (격식)
→ "Hello [First Name]," (일반)
→ "Hi [Name]," (비격식)

"항상 감사드립니다."
→ "I hope this email finds you well."
→ "Thank you for your continued support."

"바쁘신 중에 연락드려 죄송합니다."
→ "I apologize for interrupting your busy schedule."
→ "I hope I'm not catching you at a bad time."
```

#### 핵심 표현 번역 모음
```
요청:
"~해주시면 감사하겠습니다"
→ "I would greatly appreciate it if you could ~"
→ "Could you please ~?"
→ "I kindly request that you ~"

확인 요청:
"검토 후 회신 부탁드립니다"
→ "Please review and let me know your thoughts."
→ "Your feedback would be appreciated."

일정 요청:
"미팅 일정 조율 부탁드립니다"
→ "I would like to schedule a meeting at your earliest convenience."
→ "Could we find a time to connect?"

거절:
"아쉽게도 참여가 어렵습니다"
→ "Unfortunately, I am unable to attend/participate."
→ "I regret that I will not be able to ~"

감사:
"소중한 시간 내주셔서 감사드립니다"
→ "Thank you for taking the time to ~"
→ "I greatly appreciate your time and effort."
```

#### 전체 이메일 번역 예시
```
[원문 한국어]
제목: [미팅 요청] 협업 방안 논의를 위한 미팅 요청드립니다

안녕하세요, XYZ 회사 마케팅팀 김민준입니다.

귀사의 디지털 마케팅 솔루션에 관심이 있어 연락드립니다.

다름이 아니라, 저희 회사와의 협업 가능성에 대해 논의하고자
미팅을 요청드리고자 합니다.

3월 15일 또는 16일 오전 중에 30분 정도 시간이 가능하신지요?

바쁘신 중에 연락드려 죄송하며, 긍정적인 회신 기다리겠습니다.

김민준 드림

---

[번역 영어]
Subject: [Meeting Request] Request for a Meeting to Discuss Partnership Opportunities

Dear [Name],

My name is Min-jun Kim from the Marketing Team at XYZ Company.

I am reaching out as I am very interested in your company's digital marketing solutions.

I would like to request a brief meeting to explore potential partnership opportunities between our companies.

Would you be available for a 30-minute meeting on the morning of March 15th or 16th?

I apologize for any inconvenience, and I look forward to hearing from you.

Best regards,
Min-jun Kim
Marketing Team, XYZ Company
```

---

## 비즈니스 문서 번역

### 계약서 핵심 용어 영한/한영 번역
```
영어 → 한국어 주요 용어:

Party A / Party B → 갑 / 을
Whereas → 전문 (계약서 배경)
Recitals → 전문 조항
Term → 계약 기간
Termination → 해지
Governing Law → 준거법
Jurisdiction → 관할 법원
Confidential Information → 비밀 정보
Intellectual Property → 지식재산권
Force Majeure → 불가항력
Indemnification → 면책/손해배상
Warranty → 보증
Breach → 위반
Remedy → 구제 수단
Severability → 분리 가능성
Entire Agreement → 완전 합의 조항
```

### 보고서 번역 자주 쓰는 표현
```
한국어 → 영어 비즈니스 표현:

"전년 동기 대비 X% 증가"
→ "increased by X% year-over-year (YoY)"
→ "a X% increase compared to the same period last year"

"목표 대비 달성률"
→ "achievement rate vs. target"
→ "percentage of target achieved"

"주요 성과"
→ "Key Achievements" / "Highlights"

"개선 방안"
→ "Improvement Measures" / "Recommendations"

"향후 계획"
→ "Future Plans" / "Next Steps" / "Action Items"

"현황"
→ "Current Status" / "Status Update"
```

---

## 구현 가이드

### 번역 품질 향상 5가지 원칙
1. **일관성**: 같은 용어는 동일하게 번역 (용어집 관리)
2. **자연스러움**: 직역보다 의역으로 자연스럽게
3. **문화 고려**: 한국 문화 표현을 영어 문화에 맞게
4. **검증**: 원어민 검토 또는 재번역(Back-translation) 활용
5. **맥락 파악**: 전체 문서 구조 이해 후 번역

### 번역 요청 프롬프트 템플릿
```
[번역 요청 시 AI 프롬프트]
다음 한국어 비즈니스 문서를 영어로 번역해 주세요.

번역 조건:
- 수신자: {미국/영국/글로벌} 비즈니스 파트너
- 격식 수준: {Formal/Semi-formal}
- 문서 유형: {이메일/계약서/보고서}
- 특별 요청: {한국적 표현을 영어 비즈니스 문화에 맞게 현지화}

원문:
{번역할 내용}

번역 후 원문과 비교하여 누락이나 오역이 없는지 확인해 주세요.
```

---

## 고급 패턴

### 한국 특유의 표현 영어 처리 방법
```
"수고하셨습니다"
→ 이메일 끝: "Thank you for your hard work."
→ 회의 끝: "Great work today, everyone."
→ 직역 금지: "You've worked hard." (어색함)

"잘 부탁드립니다"
→ "I look forward to working with you."
→ "Thank you for your cooperation."
→ "I appreciate your assistance."

직함 처리:
"김 팀장님" → "Team Leader Kim" 또는 "Mr./Ms. Kim"
"이 부장님" → "Department Head Lee" 또는 "Mr./Ms. Lee"
→ 외국계에서는 직함보다 Mr./Ms. + 성이 일반적
```

### 문서별 번역 주의 사항
```
계약서:
- 반드시 법률 전문가 검토
- 원문과 번역본 간 충돌 시 적용 우선 순위 명시
- "원문 우선" 또는 "양 언어 동일 효력" 조항 확인

특허/기술 문서:
- 특허 용어는 공인된 번역 사용
- 창의적 번역 금지 (법적 효력 문제)

마케팅 자료:
- 직역 금지, 현지화 필수
- 한국 특유의 유머/관용구는 대체 표현 사용
```

---

## 관련 스킬

- workplace-business-email: 영문 이메일 작성 및 번역
- workplace-contract-review: 영문 계약서 검토
- workplace-sns-content: 영문 SNS 콘텐츠 작성
