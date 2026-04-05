# HWP/HWPX 워크플로 가이드

## HWP vs HWPX 형식 비교

| 항목 | HWP (구형) | HWPX (신형) |
|------|-----------|------------|
| 구조 | 바이너리 OLE2 복합 문서 | XML + ZIP 압축 |
| 파싱 난이도 | 높음 (독점 바이너리) | 낮음 (표준 XML) |
| 서식 보존 | 완전 (원본) | 완전 (XML 기반) |
| 변환 권장도 | 가능하면 HWPX로 전환 | 권장 형식 |
| 한컴오피스 | 2010 이상 지원 | 2014 이상 기본 |
| 오픈소스 지원 | 제한적 | 비교적 양호 |

**결론**: 신규 문서는 HWPX 형식으로 저장·배포 권장.

---

## Step-by-step 워크플로

### 1. HWP 읽기 → Markdown 추출

```bash
# 단일 파일
hwp read 공문.hwp --output 공문.md

# HWPX
hwp read 보고서.hwpx --output 보고서.md

# 메타데이터 포함 출력
hwp read 문서.hwp --include-metadata --output 문서.md

# 오류 발생 시 fallback 순서:
# 1) hwp-toolkit → 2) libhwp → 3) hwp5txt → 4) olefile
```

### 2. Markdown → HWPX 생성

```bash
# 권장: md2hwp 방식 (서식 보존 우수)
hwp create --method md2hwp --input 초안.md --output 결과.hwpx

# 대안: python-hwpx 방식 (단순 문서에 적합)
hwp create --method python-hwpx --input 초안.md --output 결과.hwpx

# 양식 파일 적용 (기존 서식 유지)
hwp create --method md2hwp --template 양식.hwpx --input 초안.md --output 결과.hwpx
```

### 3. HWP/HWPX → PDF 변환

```bash
# 단일 파일
hwp convert --to pdf 문서.hwp --output 문서.pdf

# 일괄 변환 (폴더 내 전체)
for f in *.hwp; do hwp convert --to pdf "$f" --output "${f%.hwp}.pdf"; done
for f in *.hwpx; do hwp convert --to pdf "$f" --output "${f%.hwpx}.pdf"; done
```

### 4. 메타데이터·구조 검사

```bash
hwp analyze 문서.hwp
# 출력: 작성자, 수정일, 페이지 수, 섹션 구조, 스타일 목록
```

---

## md2hwp vs python-hwpx 방식 비교

| 항목 | md2hwp | python-hwpx |
|------|--------|------------|
| 표 지원 | 우수 | 기본 |
| 이미지 삽입 | 지원 | 제한적 |
| 스타일 적용 | 풍부 | 단순 |
| 처리 속도 | 중간 | 빠름 |
| 의존성 | Pandoc + hwp-toolkit | python-hwpx 라이브러리 |
| 권장 용도 | 표·이미지 포함 공문 | 텍스트 중심 단순 문서 |

**권장**: 대부분의 공문서는 `md2hwp` 방식 사용.

---

## 공문서 작성 시 주의사항

### 양식 보존
- 기존 HWP 양식을 `--template` 옵션으로 지정하면 머리글·바닥글·스타일 유지
- 공문 양식(결재란, 시행일, 수신처)은 변환 후 반드시 수동 확인

### 서식 한계
- 복잡한 표 병합(셀 병합)은 변환 후 깨질 수 있음 → 한컴오피스에서 후편집
- 특수 문자(○, ●, ▶ 등)는 HWPX에서 정상 표현되나 HWP에서 깨질 수 있음
- 이미지·그림은 별도 파일로 준비 후 삽입

### 보안
- 개인정보(주민번호, 연락처) 포함 파일은 처리 후 즉시 삭제
- 내부 예산·급여 문서는 요약만 추출, 원본 파일 외부 전송 금지

---

## 일괄 처리 예시

### 폴더 내 HWP 전체 → summary.md 생성

```bash
#!/bin/bash
# batch-summary.sh
OUTPUT="summary.md"
echo "# HWP 문서 일괄 요약" > "$OUTPUT"
echo "생성일: $(date '+%Y-%m-%d')" >> "$OUTPUT"
echo "" >> "$OUTPUT"

for f in *.hwp *.hwpx; do
  [ -f "$f" ] || continue
  echo "## $f" >> "$OUTPUT"
  hwp read "$f" | head -50 >> "$OUTPUT"
  echo "" >> "$OUTPUT"
  echo "---" >> "$OUTPUT"
done

echo "완료: $OUTPUT"
```

```bash
chmod +x batch-summary.sh
./batch-summary.sh
```

### PDF 일괄 변환

```bash
#!/bin/bash
# batch-pdf.sh
mkdir -p pdf-output
for f in *.hwp *.hwpx; do
  [ -f "$f" ] || continue
  base="${f%.*}"
  hwp convert --to pdf "$f" --output "pdf-output/${base}.pdf"
  echo "변환 완료: $f → pdf-output/${base}.pdf"
done
```

---

## MCP 서버 설정

Claude Desktop `claude_desktop_config.json`에 추가:

```json
{
  "mcpServers": {
    "hwp-toolkit": {
      "command": "hwp-toolkit-mcp",
      "args": []
    }
  }
}
```

설정 후 Claude Desktop 재시작 → 대화 중 HWP 파일 직접 처리 가능.
