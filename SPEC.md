# Numberblocks Music & Lyrics Web — Task Specification (SPEC.md v2.1)

## 1. 프로젝트 개요 (Project Overview)
- **목적**: 넘버블럭스(Numberblocks)의 대표 숫자 노래, **구구단(Times Tables 1단~10단) 곱셈 노래**, 스페셜 송의 제목과 가사를 한눈에 찾아보고, 아이와 부모가 함께 읽고 따라 부를 수 있는 단일 파일 웹 애플리케이션(`index.html`).
- **핵심 원칙**: **외부 의존성 제로(Zero-Dependency)** — 외부 JS/CSS 라이브러리나 웹폰트/아이콘 CDN 없이 순수 HTML5 + CSS3 + Vanilla JS만으로 100% 동작.
- **배포 경로**: GitHub Pages (`https://calln87.github.io/numberblocks_music/`)

---

## 2. 핵심 요구사항 (v2.1 — 구구단 시리즈 및 전체 숫자곡 대폭 확충)

### 2.1 데이터 및 다국어 구성 (총 41곡: 한/영 완비 33곡 + 영어 전용 8곡)
1. **구구단 / 곱셈표 시리즈 (`times-table` 구간, 총 10곡 추가)**
   - `One Times Table` (1단), `Two Times Table` (2단 - 신발 가게), `Three Times Table` (3단 - 서커스), `Four Times Table` (4단 - 디스코), `Five Times Table` (5단 - 록스타), `Six Times Table` (6단 - 리믹스 쇼), `Seven Times Table` (7단 - 무지개 항해), `Eight Times Table` (8단 - 옥토 그루브), `Nine Times Table` (9단 - 마법 타워), `Ten Times Table` (10단 - 로켓 카운트).
   - 한/영 완비 곡(`hasKorean: true`)과 영어 원곡 전용 곡(`hasKorean: false`)을 모두 포함하여 요구사항을 충족.
2. **숫자 0 ~ 21 전 구간 완비 및 스페셜 곡 확충**
   - `0 (Zero)` 및 기존 누락되었던 `13 (Thirteen)`, `14 (Fourteen)`, `17 (Seventeen)`, `18 (Eighteen)`, `19 (Nineteen)`, `21 (Twenty-One)`을 모두 추가하여 **0부터 21, 100까지 빈 번호 없이 완비**.
   - 영어 전용 스페셜 곡(`The Numberblobs Song`, `What's the Difference?`, `Sign of the Times`, `Big Tum`, `Ten Again`, `Counting Sheep`, `How Many Ways?`, `Seven Times Table`) 포함.
3. **영어 전용 곡(EN-Only) 엣지 케이스 완벽 대응**
   - 목록 및 상단 배지에 `EN Only` 표시.
   - `한글 가사만(KO)` 모드 선택 시 빈 화면 대신 **원어(English) 가사 폴백(Fallback)** + **우리말 핵심 의미 요약 박스(`meaningKo`)** 자동 표시.

### 2.2 가사 뷰어 및 가독성 고도화
1. **4가지 가사 보기 모드 (`langMode`)**
   - `한줄 대조 (Line Sync)` / `좌우 비교 (Side-by-Side)` / `English Only (EN)` / `한글 가사만 (KO)`
2. **싱어롱(Sing-Along) 한글 발음(독음) 가이드 토글 (`showPronunciation`)**
3. **가사 글자 크기 조절 컨트롤러 (`fontScale`: `A-`, `A`, `A+`, `A++`)**

### 2.3 검색, 필터링 및 구구단 전용 탭
1. **실시간 통합 검색 & 키워드 하이라이팅 (`<mark class="hl">`)**
   - `times table`, `구구단`, `1단`~`10단`, `multiply`, 숫자, 제목, 가사, 발음 키워드 즉시 검색.
2. **숫자 구간 & 구구단 빠른 필터 (`range-chip`)**
   - `전체 구간` / `✖️ 구구단 (1단~10단)` / `숫자 0 ~ 5` / `숫자 6 ~ 10` / `숫자 11 ~ 21` / `테마 & 100 & 스페셜`

### 2.4 인터랙티브 넘버블럭 블록 조립기 (구구단 모드 지원)
1. 일반 숫자곡은 약수 배열(Factor Arrays) 변환을 지원하고, **구구단(`times-table`) 곡**은 `N × 1`부터 `N × 10`까지 곱셈 단수 버튼을 눌러 곱셈 결과 블록 배열을 직접 확인하는 인터랙티브 곱셈 테이블 조립기를 제공한다.

---

## 3. QA 검증 체크리스트
- [ ] **Zero-Dependency 검증**: 외부 `<script src="...">` 또는 `<link href="http...">`가 0개인가?
- [ ] **데이터 무결성 검증**: 총 40곡 모두 영문 가사 줄 수와 한글 발음 줄 수(및 한/영 곡의 한글 가사 줄 수)가 1:1로 정확히 일치하는가?
- [ ] **구구단 필터 및 검색 검증**: `구구단 (1단~10단)` 필터 클릭 시 10개의 Times Table 노래가 정확히 노출되고, `One Times Table` 등 검색 및 곱셈 단수 조립기(`N × 1` ~ `N × 5`)가 정상 동작하는가?
- [ ] **EN-Only 엣지 케이스 및 인터랙션 검증**: Headless Chrome DOM 시뮬레이션 전 항목 PASS 여부.
