---
name: anchor-slides
description: >
  발표자료 생성. visual-explainer(HTML), Canva MCP(PPTX), Google Slides 3가지 경로 지원.
  트리거 키워드: 발표자료, 슬라이드, 프레젠테이션, PPT, slides
---

# anchor-slides — 발표자료 생성

## 역할

목적과 대상에 따라 최적의 경로로 발표자료를 생성한다.  
3가지 경로(visual-explainer, Canva MCP, Google Slides)와 Excalidraw 다이어그램을 조합한다.

## 경로 선택

사용자에게 아래를 먼저 확인한다:
1. 발표 목적 (내부 공유 / 대외 공식 보고 / 팀 협업)
2. 편집 필요 여부 (편집 가능 파일 필요한가?)
3. 협업 필요 여부 (여러 사람이 함께 편집하는가?)

---

## Route 1 — visual-explainer (HTML 슬라이드)

**적합한 경우**: 내부 발표, 기술 브리핑, 데이터 시각화, 빠른 생성

```
/visual-explainer:generate-slides
```

**프리셋**:
- `Midnight Editorial` — 다크, 고급스러운 편집 스타일
- `Warm Signal` — 따뜻한 색조, 정책·교육 발표
- `Terminal Mono` — 개발·기술 발표용 모노스페이스
- `Swiss Clean` — 깔끔한 미니멀 레이아웃

**워크플로**:
1. 주제와 핵심 메시지 정리
2. `/visual-explainer:generate-slides` 호출
3. 프리셋 선택
4. HTML 파일 생성 → 브라우저에서 발표 또는 PDF 인쇄

---

## Route 2 — Canva MCP (편집 가능 PPTX/PDF)

**적합한 경우**: 대외 발표, 공식 보고, 브랜드 일관성 필요

**워크플로**:
1. `request-outline-review` — 아웃라인 검토 요청
2. 사용자 승인
3. `generate-design-structured` — 구조화 디자인 생성
4. `export` — PPTX 또는 PDF로 내보내기

**앵커 브랜드 적용**:
- Primary: `#2f4cb3` (딥 블루)
- Accent: `#4af2c8` (민트)
- 대학명: Cheju Halla University

---

## Route 3 — Google Slides (팀 협업)

**적합한 경우**: 팀 협업, 회의 자료, 공동 편집

**워크플로**:
1. Google Slides 링크 공유 또는 새 파일 생성
2. Claude가 슬라이드별 텍스트 콘텐츠 초안 작성
3. 팀원과 공동 편집

---

## Excalidraw (기술 다이어그램)

모든 경로에 삽입 가능한 기술 다이어그램:
- 시스템 아키텍처, 플로우차트, 조직도
- `/excalidraw` 또는 직접 Excalidraw MCP 사용

---

## 출력 형식

각 경로별 기본 출력:
- Route 1: `slides.html` (단일 파일, 브라우저 발표)
- Route 2: Canva 링크 + PPTX/PDF 다운로드
- Route 3: Google Slides URL

## 주의사항

- 슬라이드 1장 = 핵심 메시지 1개 원칙 준수
- 7±2장 권장 (너무 많으면 메시지 분산)
- 대외 발표는 반드시 Cheju Halla University 표기
- references/presentation-guide.md에서 브랜드 가이드 및 체크리스트 확인
