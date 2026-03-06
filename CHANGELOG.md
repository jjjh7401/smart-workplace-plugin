# Changelog

All notable changes to the Smart Workplace Plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.1] - 2026-03-06

### Fixed

- `plugin.json`에서 잘못된 경로 선언(`commands`, `agents`, `skills`) 제거 — 플러그인 설치 실패 원인
- `keywords` 배열에서 `한국어` 중복 항목 제거

---

## [1.0.0] - 2026-03-03

### Added

#### 슬래시 커맨드 (7종)

- `/smart-workplace:daily-report` - 일일 업무 보고서 자동 작성
- `/smart-workplace:quick-email` - 비즈니스 이메일 즉시 생성
- `/smart-workplace:resume-check` - 이력서 및 자기소개서 검토 및 개선
- `/smart-workplace:meeting-prep` - 회의 안건 정리 및 회의록 템플릿 준비
- `/smart-workplace:prompt-craft` - 업무용 AI 프롬프트 설계
- `/smart-workplace:contract-check` - 계약서 위험 조항 분석
- `/smart-workplace:biz-plan` - 사업계획서 초안 작성

#### 스킬 - 문서 작성 (6종)

- `workplace-korean-report` - 한국형 업무 보고서 작성 표준 및 서식
- `workplace-business-email` - 비즈니스 이메일 어조 및 형식 가이드
- `workplace-meeting-minutes` - 회의록 작성 표준 및 템플릿
- `workplace-proposal-writing` - 제안서 작성 구조 및 설득 전략
- `workplace-presentation-deck` - 프레젠테이션 구성 및 슬라이드 작성
- `workplace-technical-doc` - 기술 문서 작성 표준

#### 스킬 - 비즈니스 전략 (6종)

- `workplace-business-plan` - 사업계획서 작성 표준 및 투자자 설득 기법
- `workplace-contract-review` - 한국 계약서 검토 기준 및 위험 조항 분석
- `workplace-market-analysis` - 시장 분석 방법론 및 한국 시장 특성
- `workplace-financial-modeling` - 재무 모델링 및 수익 예측 방법
- `workplace-negotiation-tactics` - 한국 비즈니스 협상 전략
- `workplace-startup-toolkit` - 스타트업 창업 실무 가이드

#### 스킬 - 커리어 개발 (6종)

- `workplace-portfolio-resume` - 한국 이력서 및 자기소개서 작성 표준
- `workplace-job-interview` - 면접 준비 및 한국 직장 문화 이해
- `workplace-performance-review` - 성과 평가 작성 및 역량 개발 계획
- `workplace-salary-negotiation` - 연봉 협상 전략 및 시장 급여 분석
- `workplace-linkedin-profile` - LinkedIn 프로필 최적화 (한국 시장)
- `workplace-personal-branding` - 개인 브랜딩 전략

#### 스킬 - AI 업무 활용 (6종)

- `workplace-prompt-engineering` - 업무용 AI 프롬프트 설계 고급 기법
- `workplace-data-analysis` - 업무 데이터 분석 및 시각화 방법
- `workplace-automation-workflow` - 반복 업무 자동화 설계
- `workplace-ai-ethics` - 직장 내 AI 윤리적 활용 가이드
- `workplace-productivity-system` - 개인 생산성 시스템 구축 (GTD, PKM)
- `workplace-knowledge-management` - 팀 지식 관리 및 문서화 전략

#### 에이전트 (3종)

- `workplace-document-expert` - 업무 문서 전문가 에이전트
- `workplace-business-expert` - 비즈니스 전략 전문가 에이전트
- `workplace-career-expert` - 커리어 개발 전문가 에이전트

#### 플러그인 인프라

- `plugin.json` - 플러그인 매니페스트 및 메타데이터
- `README.md` - 한국어 설치 및 사용 가이드
- `LICENSE` - MIT 라이선스
- `CHANGELOG.md` - 변경 이력 문서

---

[1.0.0]: https://github.com/jjjh7401/smart-workplace/releases/tag/v1.0.0
