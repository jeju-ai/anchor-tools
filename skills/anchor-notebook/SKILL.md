---
name: anchor-notebook
description: >
  문서 기반 AI 요약·Q&A (Google NotebookLM 대안). 다수 문서를 기반으로 종합 분석, 요약, 질의응답.
  트리거 키워드: 문서 요약, 자료 분석, NotebookLM, 문서 Q&A, 자료 종합
---

# anchor-notebook — 문서 기반 AI 분석

## 역할

여러 문서(HWP, PDF, MD, Excel 등)를 통합 분석하는 Google NotebookLM 대안.  
Claude Desktop Projects를 활용한 즉시 사용 가능한 워크플로를 제공한다.

## Phase 1 — 즉시 사용 (Claude Desktop Projects)

### 워크플로

```
문서 수집 → (HWP 변환) → Project Knowledge 등록 → 질문/요약/비교
```

### 문서 종류별 전처리

| 형식 | 처리 방법 |
|------|----------|
| HWP/HWPX | `anchor-hwp` 스킬로 먼저 Markdown 변환 후 등록 |
| PDF | Claude Desktop에서 직접 첨부 가능 |
| Excel/CSV | CSV로 내보내기 후 등록 |
| Word | Markdown 변환 또는 직접 첨부 |
| 웹페이지 | 텍스트 복사 또는 URL 첨부 |

### Project Knowledge 등록 방법

1. Claude Desktop → Projects 탭 → 새 프로젝트 생성 (또는 기존 프로젝트 선택)
2. "Add to Project" → 문서 파일 업로드 또는 텍스트 붙여넣기
3. 여러 문서 등록 → 교차 분석, 비교, 종합 요약 가능

### 효과적인 질문 예시

```
"이 자료들의 공통점과 차이점은?"
"가장 중요한 결정 사항 3가지는?"
"[문서A]와 [문서B]를 비교해서 핵심 차이를 요약해줘"
"전체 자료에서 예산 관련 내용만 모아서 정리해줘"
"이 내용을 개조식 보고서로 변환해줘"
```

## Phase 2 — 향후 기능 (오디오 요약)

ElevenLabs MCP TTS 연동으로 오디오 요약(팟캐스트 형식) 생성 예정:

```
문서 분석 → Claude 요약 스크립트 생성 → ElevenLabs TTS → MP3 오디오
```

- 사용 사례: 이동 중 자료 청취, 회의 브리핑 오디오
- 현재 상태: 로드맵 단계 (ElevenLabs MCP 설정 후 활성화)

## 출력 형식

- **구조화 요약(MD)**: 주요 섹션별 정리, 개조식 적용
- **핵심 포인트 목록**: 불릿 형식, 우선순위 순
- **FAQ 자동 생성**: 자주 묻는 질문 형식으로 재구성
- **(향후) 오디오 MP3**: ElevenLabs 연동 시 활성화

## 주의사항

- 한 프로젝트에 너무 많은 문서 등록 시 성능 저하 가능 → 주제별로 분리
- HWP 파일은 반드시 `anchor-hwp`로 변환 후 등록 (HWP 직접 첨부 불가)
- 개인정보 포함 문서는 등록 전 마스킹 필요
- references/notebook-workflow.md에서 상세 설정 및 NotebookLM 비교 확인
