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

## 개발 노트

- CSS/JS 모두 HTML 내 인라인 (단일 파일 배포 원칙)
- 용어 데이터 리서치 소스: `_tools/research_wiki_glossary.py`
- 관련 리서치 문서: `docs/glossary-research.md`
- 이미지 추가 시: `images/chars/` 또는 `images/icons/`에 파일 추가
