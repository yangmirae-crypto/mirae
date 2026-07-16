# 제작 매뉴얼 (Production Manual) 

이 문서는 라이프스타일 멘토 Mirae Yang의 홈페이지 제작 과정을 상세히 기록하여 프로젝트의 원활한 유지보수 및 관리를 돕는 매뉴얼입니다.

## 1. 개요 및 기술 스택

본 홈페이지는 빠르고 안정적이며 유지보수가 쉬운 정적 사이트 생성을 위해 설계되었습니다.
- **정적 웹사이트 생성기(SSG):** [Hugo Extended](https://gohugo.io/) (v0.163.3+)
- **블록 프레임워크:** [Hugo Blox Builder](https://hugoblox.com/) (v2.0)
- **스타일링:** Tailwind CSS v4 (블록 프레임워크 기본 내장)
- **런타임 및 의존성 관리:** Node.js, npm, Go (Hugo 모듈 관리용)

---

## 2. 개발 환경 설정 및 설치 요구사항

로컬 장비에서 프로젝트를 빌드하고 수정하려면 다음 프로그램들의 설치가 필요합니다.

### macOS (Homebrew 사용 시)
```bash
# 필수 시스템 종속성 설치
brew install hugo node golang
```

### 프로젝트 의존성 설치
프로젝트 루트 디렉토리에서 Tailwind CSS v4 및 빌드 도구를 로컬 노드 모듈로 설치합니다.
```bash
npm install
```

---

## 3. 설정 및 맞춤화 가이드

### 3.1 사이트 아이덴티티 및 SEO 설정
`config/_default/params.yaml` 파일에서 기본 타이틀과 SEO 설명을 변경했습니다.
- **사이트 이름:** Mirae Yang
- **태그라인:** 라이프스타일 멘토 & 비즈니스 오너
- **메타 설명:** 건강한 일상과 내일의 성장을 돕는 라이프스타일 멘토, Mirae Yang입니다. 긍정적인 변화를 만드는 독서 모임과 맞춤형 건강 멘토링에 함께하세요.
- **저자 정보:** `data/authors/me.yaml` 파일에서 이름(`Mirae Yang`), 프로필 소개 및 링크를 개인 맞춤으로 변경했습니다.

### 3.2 디자인 시스템 (색상 및 폰트)
- **색상 테마:** 자연의 따뜻함(일출, 장미, 라일락)을 연상시키는 톤으로 설정되었습니다.
  - `primary` (일출/장미 톤): `#E05A47`
  - `secondary` (라일락 톤): `#D291BC`
- **폰트 테마:** 헤드라인에는 감성적이고 신뢰감을 주는 명조체(Serif), 본문에는 가독성이 높은 고딕체(Sans-serif) 구조를 혼합한 `editorial` 폰트 팩을 설정했습니다.
  - `typography.pack: "editorial"`

### 3.3 메뉴 구성
`config/_default/menus.yaml`에서 상단 네비게이션바 및 하단 푸터 영역의 링크를 한글화하고 알맞게 재구성했습니다.
- **상단 메뉴:** 홈, 소개, 주요활동, 서비스안내, 블로그, 후기, FAQ, 문의하기
- **푸터 메뉴:** 서비스, 커뮤니티, 법적고지 세부 링크

---

## 4. 콘텐츠 편집 방법

모든 사이트 콘텐츠는 마크다운(Markdown) 형태로 저장되어 직접 편집이 가능합니다.

### 4.1 메인 랜딩 페이지 (`content/_index.md`)
각 세션이 독립적인 블록(Block) 형태로 쌓여 있습니다.
- `hero`: 대문 영역 (헤드라인, 서브텍스트, 커뮤니티 참여 버튼)
- `markdown (id: about)`: 소개 글
- `features (id: activities)`: 주요 활동 포트폴리오 그리드 갤러리
- `features (id: services)`: 라이프스타일 멘토링, 북클럽 등 서비스 가이드
- `content-collection (id: blog)`: 최근 작성한 블로그 글 표시 영역
- `testimonials`: 참가자 추천사 및 후기 슬라이더
- `faq`: 자주 묻는 질문 아코디언
- `contact-info (id: contact)`: 연락처 안내 및 통합 문의 양식 (이름, 이메일, 제목, 메시지 폼 포함)

### 4.2 블로그 포스트 (`content/blog/`)
새로운 글을 작성할 때는 아래와 같이 새 하위 폴더와 `index.md` 파일을 생성하여 관리합니다.
- 예: `content/blog/[포스트명]/index.md`

**머리말(Front Matter) 템플릿:**
```yaml
---
title: "포스트 제목"
date: 2026-07-02
authors:
  - me
tags:
  - 태그1
  - 태그2
categories:
  - 카테고리
summary: "글 목록 화면에 노출될 요약본 설명글"
---
```

---

## 5. 실행 및 빌드 명령어

### 로컬 개발 서버 구동 (실시간 미리보기)
Tailwind CSS의 경로가 정상적으로 동작하도록 로컬 환경 변수 PATH에 `.bin` 폴더를 포함하여 실행합니다.
```bash
PATH=$PATH:$(pwd)/node_modules/.bin hugo server --port=1313
```
- 브라우저 주소: `http://localhost:1313/`
- 코드를 수정하면 브라우저가 실시간으로 자동 리로드됩니다.

### 운영용 정적 웹사이트 빌드
사이트 배포를 위한 최종 정적 HTML 파일을 빌드합니다.
```bash
PATH=$PATH:$(pwd)/node_modules/.bin hugo
```
- 결과물은 `public/` 디렉토리에 정적으로 생성되며, 이 폴더의 내용을 웹 호스팅 서버에 그대로 업로드하면 서비스가 제공됩니다.
