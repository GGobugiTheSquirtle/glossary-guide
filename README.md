# glossary-guide

어나더에덴(Another Eden) 다국어 용어집/도감. EN/KO/JP 3개 언어로 캐릭터, 스킬, 아이템 등의 용어를 검색하고 카테고리별로 필터링하는 SPA.

## Tech Stack

- 순수 HTML + inline CSS + vanilla JS (빌드 도구 없음)
- 다크 테마 UI
- 배포 준비 중 (아래 참고)

## 구조

```
glossary-guide/
├── index.html          # SPA 전체 (789줄, ~30KB)
└── images/
    ├── chars/          # 캐릭터 이미지 32개
    └── icons/          # 아이콘 이미지 27개
```

## 동작 방식

### 데이터
- index.html 내부에 JS로 인라인된 용어 데이터
- 다국어 구조: 각 용어에 EN/KO/JP 텍스트 포함

### 주요 기능
- **다국어 검색**: EN, KO, JP 텍스트 동시 검색
- **카테고리 태그 필터**: 용어 종류별 필터링
- **원소 색상 체계**: fire/water/wind/earth/thunder/shade/crystal 색상 변수 정의
- **캐릭터 이미지 연동**: chars/ 폴더 이미지 표시

### 디자인
- 다크 테마 (`--bg: #13131a`)
- CSS accent(보라), gold 포인트
- EN/KO/JP 언어별 색상 구분
- 헤더 gradient: `#0d0d1a` ~ `#1a1a3e` ~ `#0f2860`

## 배포

> **Git repo 미초기화 상태** -- GitHub Pages 배포 불가.
> 배포하려면 `git init` + GitHub repo 생성 + Pages 설정 필요.

## 「효과」 카테고리 (2026-10-30)

스킬 효과 75개(고유 용어 59 · 능력치 16)를 영·일·한으로. 카드마다 정의 · 함수 꼴 · 쓰는 캐릭터 수.

- 정본: `effects_src.json` — 이름 · 정의 · 근거 절만 사람이 고친다
- 빌드: `PYTHONUTF8=1 py -3.14 _tools/glossary/build_effects.py` (워크스페이스 루트) → `index.html` 의 `<EFFECTS>` 구간
  - 한국어 이름 · 함수 꼴 정본 = 카페 딩님 스킬 DB(`_archive/ding-skill-searcher/`, 출처 표기 조건 — 화면에 표기)
    DB_효과 한 줄(효과 동사 · 효과 상세 · 대상 · 확률 · 저항 무시 · 효과량 · 턴 · 횟수)을 모아 `상태 효과 부여(도발, 대상, 턴: 1~5·자연 해제, 저항 무시?)` 꼴로.
    `?` = 일부 줄에만 있는 인자. 딩님 DB 에 없는 효과는 character-guide 의 파싱된 효과 단위로 대신
  - 쓰는 캐릭터 = 딩님 DB · 한(공지 스킬문) · 영(위키) · 일(game-info 스킬 효과 줄) 중 하나라도 나오는 캐릭터
  - 이름 근거 0 인 언어는 `ko_note` 로 「미확인」 표시
- 정의 근거: game-info 「状態効果まとめ」(`_archive/effect-glossary/`) · anothereden.wiki Status Effects

## 개발 노트

- CSS/JS 모두 HTML 내 인라인 (단일 파일 배포 원칙)
- 용어 데이터 리서치 소스: `_tools/research_wiki_glossary.py`
- 관련 리서치 문서: `docs/glossary-research.md`
- 이미지 추가 시: `images/chars/` 또는 `images/icons/`에 파일 추가
