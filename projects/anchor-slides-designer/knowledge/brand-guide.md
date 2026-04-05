# 앵커(RISE) 비주얼 아이덴티티 가이드

## 브랜드 개요

- **사업명**: 앵커(지역성장 인재양성체계) / RISE(Regional Innovation System & Education)
- **주관**: 제주한라대학교 (Cheju Halla University, CHU)
- **영문 약칭**: CHU RISE Anchor

---

## 색상 시스템

### 주요 색상

| 이름 | HEX | RGB | 용도 |
|------|-----|-----|------|
| Primary Blue | `#2f4cb3` | 47, 76, 179 | 제목, 주요 헤더, 아이콘 |
| Accent Mint | `#4af2c8` | 74, 242, 200 | 강조, 데이터 포인트, 버튼 |
| Deep Navy | `#1a2856` | 26, 40, 86 | 다크 배경, 사이드바 |
| Sky Blue | `#6b9fff` | 107, 159, 255 | 보조 강조, 차트 |

### 중립 색상

| 이름 | HEX | 용도 |
|------|-----|------|
| Dark BG | `#0f1923` | 다크 테마 슬라이드 배경 |
| Light BG | `#f8f9fc` | 라이트 테마 슬라이드 배경 |
| Text Dark | `#1a1a2e` | 라이트 배경 위 본문 |
| Text Light | `#ffffff` | 다크 배경 위 본문 |
| Neutral Gray | `#6b7280` | 캡션, 보조 텍스트 |
| Border | `#e5e7eb` | 구분선, 테두리 |

### 색상 사용 원칙

- Primary Blue는 슬라이드당 1~2개 요소에만 사용 (남용 금지)
- Accent Mint는 진짜 강조가 필요한 1~3개 요소에만 사용
- 배경색과 텍스트 색상 대비: WCAG AA 기준 (4.5:1 이상) 준수
- 다크 테마(`#0f1923`) + 민트(`#4af2c8`) 조합: 기술·데이터 발표에 적합

---

## 타이포그래피

### 폰트 패밀리

| 언어 | 폰트 | 웨이트 | 다운로드 |
|------|------|--------|---------|
| 국문 제목 | Noto Sans KR | 700 (Bold) | Google Fonts |
| 국문 본문 | Noto Sans KR | 400 (Regular) | Google Fonts |
| 국문 강조 | Noto Sans KR | 600 (SemiBold) | Google Fonts |
| 영문 제목 | Inter | 700 (Bold) | Google Fonts |
| 영문 본문 | Inter | 400 (Regular) | Google Fonts |
| 코드/데이터 | JetBrains Mono | 400 | JetBrains |

### 폰트 크기 (슬라이드 기준, 1920×1080)

| 요소 | 크기 | 웨이트 |
|------|------|--------|
| 슬라이드 제목 | 36~44pt | Bold |
| 섹션 헤더 | 28~32pt | SemiBold |
| 본문 텍스트 | 20~24pt | Regular |
| 캡션/주석 | 14~16pt | Regular |
| 데이터 강조 숫자 | 48~72pt | Bold |

**최소 기준**: 본문 18pt 이상, 캡션 12pt 이상 (프로젝터 가독성)

---

## 로고 사용 규칙

### 로고 배치

- **표지 슬라이드**: 중앙 하단 또는 우측 하단에 CHU + RISE/앵커 로고 배치
- **내부 슬라이드**: 우측 상단 작은 크기로 삽입 (선택적)
- **마지막 슬라이드**: 중앙 배치, 연락처와 함께

### 로고 여백 규칙

- 로고 주변: 로고 높이의 50% 이상 여백 확보
- 배경색과 충분한 대비 유지
- 로고 변형(회전, 색상 변경, 왜곡) 금지

### 대학명 표기

| 상황 | 표기 |
|------|------|
| 영문 공식 | Cheju Halla University |
| 영문 약칭 | CHU |
| 국문 | 제주한라대학교 |
| 금지 표기 | Jeju Halla University, Jeju Halla Univ |

---

## 슬라이드 템플릿

### 표지 슬라이드

```
배경: #0f1923 (다크) 또는 #f8f9fc (라이트)
제목: 40~44pt, Noto Sans KR Bold, 색상 #ffffff 또는 #2f4cb3
부제목: 24pt, Regular, #6b7280
발표자: 20pt, SemiBold
날짜/행사: 18pt, Regular, #4af2c8 (강조) 또는 #6b7280
로고: 하단 중앙 또는 우측 하단
```

### 콘텐츠 슬라이드

```
상단: 슬라이드 제목 (36pt, Bold, #2f4cb3)
      좌측 경계선: 4px solid #4af2c8 (선택적)
본문: 좌측 또는 양분할 레이아웃
      텍스트 20~24pt, Regular
하단: 슬라이드 번호 (우측 하단, 14pt, #6b7280)
```

### 데이터 슬라이드

```
강조 숫자: 60~72pt, Bold, #2f4cb3 또는 #4af2c8
단위: 24pt, Regular, #6b7280
설명: 18pt, Regular
차트 색상: Primary #2f4cb3, Secondary #4af2c8, Others #6b9fff, #e5e7eb
```

---

## 아이콘 & 일러스트레이션

- 아이콘 스타일: Outlined (두께 1.5~2px), 둥근 모서리
- 권장 라이브러리: Heroicons, Phosphor Icons, Lucide
- 색상: Primary Blue 또는 Accent Mint 단색
- 크기: 본문 아이콘 24×24px, 강조 아이콘 48×48px

---

## 차트 & 데이터 시각화

### 색상 순서 (차트 시리즈)

1. `#2f4cb3` (Primary Blue)
2. `#4af2c8` (Accent Mint)
3. `#6b9fff` (Sky Blue)
4. `#a78bfa` (Purple)
5. `#f59e0b` (Amber)

### 차트 유형별 권장

| 데이터 유형 | 권장 차트 |
|------------|---------|
| 예산 집행률 | 도넛 차트 + 중앙 수치 |
| 연도별 추이 | 라인 차트 |
| 항목 비교 | 가로 막대 차트 |
| 구성 비율 | 파이/도넛 차트 |
| 성과 달성률 | 게이지 또는 프로그레스 바 |
| 지역 분포 | 지도 시각화 |
