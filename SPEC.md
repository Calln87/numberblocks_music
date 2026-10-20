# Numberblocks Music & Lyrics Web — Task Specification (SPEC.md v2.2)

## 1. 프로젝트 개요 (Project Overview)
- **목적**: 넘버블럭스(Numberblocks)의 대표 숫자 노래, **구구단(Times Tables 1단~10단) 곱셈 노래**, 슈퍼히어로 옥토블럭 테마송 2종 및 스페셜 송의 제목과 가사를 한눈에 찾아보고, 아이와 부모가 함께 읽고 따라 부를 수 있는 단일 파일 웹 애플리케이션(`index.html`).
- **핵심 원칙**: **외부 의존성 제로(Zero-Dependency)** — 외부 JS/CSS 라이브러리나 웹폰트/아이콘 CDN 없이 순수 HTML5 + CSS3 + Vanilla JS만으로 100% 동작.
- **배포 경로**: GitHub Pages (`https://calln87.github.io/numberblocks_music/`)

---

## 2. 핵심 요구사항 (v2.2 — 공식 에피소드 정식 풀버전 가사화 및 옥토블럭 2종 분리)

### 2.1 데이터 및 다국어 구성 (총 42곡: 한/영 완비 34곡 + 영어 전용 8곡)
1. **정식 에피소드 풀버전(Multi-Stanza) 가사 전면 확장**
   - 기존의 요약형 2절 가사를 BBC CBeebies 공식 방영 에피소드의 전체 가사로 전면 확장:
     - `One (One Wonderful World)`: 7절 전체 (솔로 선언, 빨간 사과, 하나의 해와 달, 다 함께 부르는 합창까지 완비)
     - `Two (Everything is Better with Two)`: 7절 전체 (신발, 장갑, 짝꿍, 오렌지 반쪽, 둘이서 함께 춤추는 장면까지 완비)
     - `Three — 1, 2, 3, Everybody Look at Me!`: 5절 전체 (저글링, 트라이앵글 변신, 빨강/주황/노랑 광대 쇼, 깜짝 등장까지 완비)
     - `Four (Have You Met Me Before?)`: 5절 전체 (정사각형 네모, 공 굴리기, 넷이서 춤추는 디스코 완비)
     - `Five (High Five!)`: 6절 전체 (하이파이브 록밴드 무대, 다섯 별, 손가락 카운트 완비)
     - `Six (Roll the Dice / Make the Shape!)`: 5절 전체 (주사위 점 여섯 개, 점박이 곤충, 블록 배열 놀이 완비)
     - `Seven (I'm Lucky Number Seven)`: 6절 전체 (무지개 일곱 색깔, 빨주노초파남보 노래 완비)
     - `Nine (Three Rows of Three Make Nine)`: 5절 전체 (3x3 정사각형, 재채기하면 1+8 또는 2+7로 분해되는 에피소드 디테일 완비)
     - `Ten (I'm One Big Perfect Ten / Rocket)`: 5절 전체 (두 손 번쩍 10개 손가락, 로켓 발사 카운트다운 완비)
     - `One Times Table (Fun Times One Times Table)`: 4절 전체 인트로/합창 완비
     - `Two Times Table (Two Times Shoe Shop)`: 4절 전체 신발 가게 인트로/합창 완비
2. **사용자 요청 옥토블럭 노래 2종 완벽 분리 및 탑재**
   - `Octoblock — 🐙 Octoblock — 나는 옥토블럭!`: 시즌 2 에피소드 3 첫 등장 및 슈퍼 영웅 탄생 테마 (6절 풀버전)
   - `The Octoblock Song! — 🐙 The Octoblock Song!`: 옥토블럭 단독 슈퍼히어로 특공대 테마송 (5절 풀버전)
3. **구구단 / 곱셈표 시리즈 (`times-table` 구간, 총 10곡 완비)**
   - `One Times Table` (1단), `Two Times Table` (2단), `Three Times Table` (3단), `Four Times Table` (4단), `Five Times Table` (5단), `Six Times Table` (6단), `Seven Times Table` (7단), `Eight Times Table` (8단), `Nine Times Table` (9단), `Ten Times Table` (10단).
4. **숫자 0 ~ 21 전 구간 완비 및 스페셜 곡 확충**
   - `0 (Zero)`부터 `21 (Twenty-One)`, `100 (One Hundred)`까지 빈 번호 없이 완비.
   - 영어 전용 스페셜 곡 8곡(`The Numberblobs Song`, `What's the Difference?`, `Sign of the Times`, `Big Tum`, `Ten Again`, `Counting Sheep`, `How Many Ways?`, `Seven Times Table`) 포함.
5. **영어 전용 곡(EN-Only) 엣지 케이스 완벽 대응**
   - 목록 및 상단 배지에 `EN Only` 표시.
   - `한글 가사만(KO)` 모드 선택 시 빈 화면 대신 **원어(English) 가사 폴백(Fallback)** + **우리말 핵심 의미 요약 박스(`meaningKo`)** 자동 표시.

### 2.2 가사 뷰어 및 가독성 고도화
1. **4가지 가사 보기 모드 (`langMode`)**
   - `한줄 대조 (Line Sync)` / `좌우 비교 (Side-by-Side)` / `English Only (EN)` / `한글 가사만 (KO)`
2. **싱어롱(Sing-Along) 한글 발음(독음) 가이드 토글 (`showPronunciation`)**
3. **가사 글자 크기 조절 컨트롤러 (`fontScale`: `A-`, `A`, `A+`, `A++`)**

### 2.3 검색, 필터링 및 구구단 전용 탭
1. **실시간 통합 검색 & 키워드 하이라이팅 (`<mark class="hl">`)**
   - `times table`, `구구단`, `1단`~`10단`, `octoblock`, `everybody look at me`, 숫자, 제목, 가사, 발음 키워드 즉시 검색.
2. **숫자 구간 & 구구단 빠른 필터 (`range-chip`)**
   - `전체 구간` / `✖️ 구구단 (1단~10단)` / `숫자 0 ~ 5` / `숫자 6 ~ 10` / `숫자 11 ~ 21` / `테마 & 100 & 스페셜`

### 2.4 인터랙티브 넘버블럭 블록 조립기 (구구단 모드 지원)
1. 일반 숫자곡은 약수 배열(Factor Arrays) 변환을 지원하고, **구구단(`times-table`) 곡**은 `N × 1`부터 `N × 10`까지 곱셈 단수 버튼을 눌러 곱셈 결과 블록 배열을 직접 확인하는 인터랙티브 곱셈 테이블 조립기를 제공한다.

---

## 3. QA 검증 체크리스트
- [x] **Zero-Dependency 검증**: 외부 `<script src="...">` 또는 `<link href="http...">`가 0개인가? (PASS)
- [x] **데이터 무결성 검증**: 총 42곡 모두 영문 가사 줄 수와 한글 발음 줄 수(및 한/영 곡의 한글 가사 줄 수)가 1:1로 정확히 일치하는가? (PASS, mismatch=0)
- [x] **정식 풀버전 가사 검증**: One(7절), Two(7절), Three(5절), Octoblock 2종(각 6절/5절) 등 정식 에피소드 풀버전 가사가 탑재되었는가? (PASS)
- [x] **구구단 필터 및 검색 검증**: `구구단 (1단~10단)` 필터 클릭 시 10개의 Times Table 노래가 정확히 노출되고, 곱셈 단수 조립기(`N × 1` ~ `N × 10`)가 정상 동작하는가? (PASS)
- [x] **EN-Only 엣지 케이스 및 인터랙션 검증**: Headless Chrome DOM 시뮬레이션 전 항목 PASS (`allPassed: true`)
