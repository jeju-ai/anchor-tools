---
name: anchor-hwp
description: >
  HWP/HWPX 공문서 읽기·생성·변환. hwp-toolkit 래퍼 스킬. 한국 공공기관 문서 처리.
  트리거 키워드: HWP 읽기, HWP 변환, 공문 변환, 한글 파일, hwp, hwpx
---

# anchor-hwp — HWP/HWPX 문서 처리

## 역할

한국 공공기관 표준 문서 형식인 HWP/HWPX 파일을 읽고, 생성하고, 변환한다.  
hwp-toolkit을 래핑하여 Claude와의 통합 워크플로를 제공한다.

## 작동 방식

### Read (읽기)

`hwp-toolkit`의 `hwp read` 명령으로 HWP/HWPX 텍스트를 Markdown으로 추출한다.

```bash
hwp read document.hwp --output document.md
hwp read document.hwpx --output document.md
```

### Create (생성)

Markdown → HWPX 변환은 `md2hwp` 방식을 권장한다 (서식 보존 우수).

```bash
hwp create --method md2hwp --input draft.md --output output.hwpx
# 대안: python-hwpx 방식
hwp create --method python-hwpx --input draft.md --output output.hwpx
```

### Convert (변환)

HWP/HWPX → PDF 변환:

```bash
hwp convert --to pdf document.hwp --output document.pdf
hwp convert --to pdf document.hwpx --output document.pdf
```

### Analyze (분석)

메타데이터·구조 검사:

```bash
hwp analyze document.hwp
```

## Fallback 체인

1. hwp-toolkit (기본)
2. libhwp
3. hwp5txt
4. olefile (최후 수단, 텍스트만 추출)

## MCP 연동

hwp-toolkit MCP 서버를 통해 Claude Desktop에서 직접 HWP 파일 조작 가능.  
MCP 설정 후 별도 CLI 없이 대화 중 HWP 읽기·생성·변환 수행.

## 일반 워크플로

### 공문 수신 처리
```
공문 수신(HWP) → hwp read → Markdown 추출 → Claude 요약 → Slack 공유
```

### 공문 작성
```
Claude 개조식 초안(MD) → hwp create --method md2hwp → HWPX 생성 → 한컴오피스 최종 편집
```

## 주의사항

- HWPX 형식 권장 (XML 기반, 서식 보존율 높음)
- 복잡한 표·그림이 포함된 HWP는 수동 후편집 필요
- 개인정보(주민번호, 연락처) 포함 파일 처리 시 보안 주의
- references/hwp-workflow.md에서 상세 워크플로 및 방식 비교 확인
