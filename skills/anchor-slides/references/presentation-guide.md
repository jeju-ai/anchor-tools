# 앵커 발표자료 가이드

## 브랜드 가이드라인

### 색상 팔레트

| 역할 | HEX | 용도 |
|------|-----|------|
| Primary | `#2f4cb3` | 제목, 강조 헤더, 주요 아이콘 |
| Accent | `#4af2c8` | 하이라이트, 데이터 포인트, CTA |
| Dark BG | `#0f1923` | 다크 테마 배경 |
| Light BG | `#f8f9fc` | 라이트 테마 배경 |
| Text Dark | `#1a1a2e` | 본문 텍스트 |
| Text Light | `#ffffff` | 다크 배경 위 텍스트 |
| Neutral | `#6b7280` | 보조 텍스트, 캡션 |

### 폰트

| 용도 | 국문 | 영문 |
|------|------|------|
| 제목 | Noto Sans KR Bold | Inter Bold |
| 본문 | Noto Sans KR Regular | Inter Regular |
| 데이터/코드 | D2Coding | JetBrains Mono |
| 강조 | Noto Sans KR SemiBold | Inter SemiBold |

### 로고 사용 규칙

- 제주한라대학교 로고: 좌측 상단 또는 우측 하단
- 영문 표기: **Cheju Halla University** (Jeju Halla 사용 금지)
- RISE/앵커 로고: 표지 슬라이드에만 사용
- 로고 주변 여백: 로고 높이의 50% 이상 확보

---

## 슬라이드 구성 원칙

### 핵심 원칙

1. **1 slide = 1 message**: 슬라이드 1장에 핵심 메시지 하나만
2. **7±2장 권장**: 5~9장이 최적 (30분 발표 기준)
3. **제목 = 결론**: 슬라이드 제목에 핵심 주장 또는 결론 기재
4. **데이터는 시각화**: 표보다 차트, 숫자보다 비율
5. **여백 확보**: 콘텐츠가 슬라이드 면적의 70% 이하

### 구성 순서

```
1. 표지 (제목, 발표자, 날짜, 행사명)
2. 목차 (선택적 — 10장 이상일 때)
3. 현황/배경 (Why)
4. 주요 내용 (What)
5. 추진 방향/계획 (How)
6. 기대 효과/성과 (So what)
7. 마무리/Q&A
```

---

## 도구별 사용법

### Route 1: visual-explainer

```
1. Claude Code에서 /visual-explainer:generate-slides 호출
2. 주제와 핵심 내용 입력
3. 프리셋 선택:
   - Midnight Editorial → 고급스러운 다크 테마
   - Warm Signal → 정책/교육 발표 (따뜻한 톤)
   - Terminal Mono → 기술/개발 발표
   - Swiss Clean → 깔끔한 미니멀
4. HTML 파일 생성 확인
5. 브라우저 전체화면(F11)으로 발표 또는 Ctrl+P → PDF 저장
```

### Route 2: Canva MCP

```
1. Canva MCP 도구 활성화 확인
2. request-outline-review 호출 → 아웃라인 제출
3. 피드백 반영 후 승인
4. generate-design-structured 호출 → 디자인 생성
5. export 호출 → PPTX 또는 PDF 선택
6. 앵커 브랜드 키트 적용 확인 (색상, 폰트)
```

### Route 3: Google Slides

```
1. slides.google.com → 새 프레젠테이션 생성
2. Claude에게 슬라이드별 콘텐츠 초안 요청
3. 슬라이드 번호별로 텍스트 복사·붙여넣기
4. 팀원과 공유 링크로 협업
```

### Excalidraw 다이어그램

```
1. /excalidraw 또는 Excalidraw MCP 도구 사용
2. 시스템 구조, 플로우차트, 조직도 등 작성
3. PNG/SVG로 내보내기 → 슬라이드에 삽입
4. 다크 배경 슬라이드: 배경 투명 PNG 사용
```

---

## 발표자료 최종 체크리스트

### 콘텐츠
- [ ] 모든 슬라이드에 명확한 제목/메시지
- [ ] 수치와 날짜 최종 확인
- [ ] 대학명 영문 표기: Cheju Halla University
- [ ] 출처 표기 (데이터, 인용문)
- [ ] 보안 정보(미공개 예산, 개인정보) 포함 여부 확인

### 디자인
- [ ] 폰트 크기: 제목 28pt 이상, 본문 18pt 이상
- [ ] 색상 대비: WCAG AA 기준 (4.5:1 이상)
- [ ] 이미지 해상도: 최소 1920×1080 (Full HD)
- [ ] 브랜드 색상(`#2f4cb3`, `#4af2c8`) 일관 적용

### 발표 전
- [ ] 프로젝터/화면 공유 테스트
- [ ] 폰트 내장 또는 시스템 폰트 확인
- [ ] PDF 백업본 준비
- [ ] 발표 시간 리허설 (1장 = 2~3분 기준)
