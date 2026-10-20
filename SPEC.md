# Numberblocks Music & Lyrics Web — Task Specification (SPEC.md v2.3)

## 1. 프로젝트 개요 (Project Overview)
- **목적**: 넘버블럭스(Numberblocks)의 대표 숫자 노래(0~21, 100), **구구단(Times Tables 1단~10단) 곱셈 노래**, 슈퍼히어로 옥토블럭 공식 9절 풀버전 및 스페셜 송의 제목과 가사를 한눈에 찾아보고, 아이와 부모가 함께 읽고 따라 부를 수 있는 단일 파일 가사 전문 웹 애플리케이션(`index.html`).
- **핵심 원칙**: **외부 의존성 제로(Zero-Dependency)** — 외부 JS/CSS 라이브러리나 웹폰트/아이콘 CDN 없이 순수 HTML5 + CSS3 + Vanilla JS만으로 100% 동작.
- **UI UX 방향성**: **가사 가독성과 싱어롱 편의성에 집중** — 블록 인터랙티브 조립기 UI를 제거하고, 화면 전체를 깔끔하고 큼직한 가사 뷰어(한줄 대조, 발음 가이드, 폰트 조절)에 최적화.
- **배포 경로**: GitHub Pages (`https://calln87.github.io/numberblocks_music/`)

---

## 2. 핵심 요구사항 (v2.3)

### 2.1 옥토블럭(Octoblock) 공식 에피소드 가사 9절 풀버전 완벽 반영
- 사용자 제공 정식 방영 에피소드 스크립트를 100% 반영하여 총 9개 절(Section) 완비:
  1. **Intro**: "I'm Eight. But you can call me... Octoblock!"
  2. **🧗 Octoblock, climb!**: 높은 벽 타고 오르기
  3. **🕷️ Octoblock, crawl!**: 기둥 세우기 및 으스스한 네모 거미 '스파이더블럭(Spiderblock)' 변신
  4. **🏃 Octoblock, run!**: 눈 깜짝할 사이에 쌩 달려가는 초고속 달리기
  5. **🐙 여덟 개의 다리를 가진 영웅!**: 튼튼하고 네모난 문어 영웅
  6. **🏊 Octoblock, swim!**: 지네처럼 빠른 고속 수영
  7. **🤗 팔이 여덟 개?!**: 여덟 팔로 꼭 안아주는 매력
  8. **🧶🍽️ 못하는 게 없는 옥토블럭**: 포근한 털실 담요, 8코스 요리, 세상 최고의 간질간질 대장(Tickler)
  9. **⭐ 옥토블럭은 뭐든 할 수 있어!**: 공 8개 저글링, 스케이트, 혼자서 완성하는 1인 조정팀, 최고의 춤 솜씨와 엔딩

### 2.2 블록 인터랙티브 UI 제거 및 가사 집중 모드
- 직사각형 약수 배열 조립기 및 구구단 블록 조립기를 제거하여, 페이지 로딩 속도를 극대화하고 사용자가 가사와 번역을 읽는 데만 온전히 집중할 수 있도록 UI를 간결하게 정리.

### 2.3 데이터 및 다국어 구성 (총 42곡: 한/영 완비 34곡 + 영어 전용 8곡)
- **대표곡 정식 풀버전(Multi-Stanza) 가사 검증 및 탑재**:
  - `One (One Wonderful World)`: 7절 전체
  - `Two (Everything is Better with Two)`: 7절 전체
  - `Three — 1, 2, 3, Everybody Look at Me!`: 5절 전체
  - `Four (Have You Met Me Before?)`: 5절 전체
  - `Five (High Five!)`: 6절 전체
  - `Six (Roll the Dice / Make the Shape!)`: 5절 전체
  - `Seven (I'm Lucky Number Seven)`: 6절 전체
  - `Octoblock — 🐙 Octoblock — 나는 옥토블럭!`: 9절 전체 공식 가사
  - `The Octoblock Song! — 🐙 The Octoblock Song!`: 5절 전체 슈퍼히어로 테마송
  - `Nine (Three Rows of Three Make Nine)`: 5절 전체
  - `Ten (I'm One Big Perfect Ten / Rocket)`: 5절 전체
  - `One Times Table`, `Two Times Table` 포함 10개 구구단 노래
- **영어 전용 곡(EN-Only) 엣지 케이스 대응**:
  - `한글 가사만(KO)` 모드 선택 시 영어 원문 가사 폴백 + `meaningKo` 우리말 곡 해설 자동 표시.

### 2.4 가사 뷰어 및 사용자 편의성
- 4가지 가사 보기 모드 (`한줄 대조`, `좌우 비교`, `EN Only`, `KO Only`)
- 싱어롱 한글 발음(독음) 가이드 토글
- 가사 글자 크기 4단계 조절 (`A-`, `A`, `A+`, `A++`)
- 실시간 키워드 하이라이팅 통합 검색

---

## 3. QA 검증 체크리스트
- [x] **Zero-Dependency 검증**: 외부 script/link 0건 (PASS)
- [x] **데이터 무결성 검증**: 42곡 전곡 영문/발음/한글 줄 수 1:1 완벽 매칭 (PASS)
- [x] **옥토블럭 정식 9절 가사 무결성 검증**: Spiderblock, 지네, 8코스 요리, 조정팀 등 핵심 라인 전수 검증 (PASS)
- [x] **블록 인터랙티브 UI 제거 검증**: visualizer/stage 요소 제거 및 순수 가사 뷰 확인 (PASS)
- [x] **헤드리스 브라우저 테스트**: Chrome headless DOM 시뮬레이션 11개 전 항목 PASS (`allPassed: true`)
