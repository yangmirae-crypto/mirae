# 문제보고서 (Troubleshooting Report)

이 문서는 프로젝트 개발 및 빌드 과정에서 발생했던 다양한 환경 이슈와 템플릿 컴파일 오류의 원인 및 이에 대한 구체적인 해결 방법을 정리한 보고서입니다.

---

## 1. Preact 패키지 미설치로 인한 빌드 오류

### 문제 증상 (Symptom)
처음 `hugo server` 실행 시 JSX 트랜스폼 도중 아래와 같은 모듈 참조 에러가 다량 발생하며 빌드가 중단됨:
```text
ERROR js.Build failed: ".../client.jsx": Could not resolve "preact/jsx-runtime"
ERROR js.Build failed: ".../Icon.jsx": Could not resolve "preact"
```

### 원인 (Cause)
Hugo Blox의 최신 테마 블록 컴포넌트(JSX/Preact 기반)는 클라이언트 렌더링에 `preact` 의존성을 필수적으로 요구합니다. 하지만 로컬 환경 설정 단계에서 `npm install`을 실행하지 않아 `node_modules`에 필요한 종속 라이브러리들이 존재하지 않았습니다.

### 해결 방법 (Solution)
프로젝트 루트에서 npm을 사용해 패키지를 설치하여 의존성을 보완했습니다.
```bash
npm install
```

---

## 2. Tailwind CSS CLI 실행 바이너리 누락 오류

### 문제 증상 (Symptom)
Preact 패키지 문제를 해결한 후 빌드 중 다음과 같은 에러가 발생함:
```text
TAILWINDCSS: failed to transform "/css/_entry.css" (text/css). 
You need to install TailwindCSS CLI.
binary with name "tailwindcss" not found in PATH
```

### 원인 (Cause)
Tailwind CSS v4를 사용하는 본 템플릿의 CSS 컴파일을 위해 Hugo가 시스템 환경 변수 `PATH`에서 `tailwindcss` 바이너리를 탐색하지만, 로컬 패키지 매니저로 설치된 `tailwindcss`는 전역 PATH가 아닌 `./node_modules/.bin/` 안에만 설치되어 있어 발생한 문제입니다.

### 해결 방법 (Solution)
명령어 실행 전 환경 변수 `PATH`에 현재 디렉토리 내의 `node_modules/.bin` 상대 경로를 명시적으로 추가하여 바이너리를 감지하게 함으로써 문제를 해결했습니다.
```bash
PATH=$PATH:$(pwd)/node_modules/.bin hugo server
```

---

## 3. 로컬 서버 포트 충돌 오류 (Address already in use)

### 문제 증상 (Symptom)
빌드 명령어를 연이어 다시 실행할 때 다음 포트 바인딩 에러가 나타남:
```text
ERROR command error: server startup failed: listen tcp 127.0.0.1:1313: bind: address already in use
```

### 원인 (Cause)
백그라운드에서 동일한 포트(`1313`)로 로컬 테스트 서버가 이미 기동되어 있는 상태에서 추가로 동일한 포트로 서버를 띄우려고 할 때 충돌이 발생한 것입니다.

### 해결 방법 (Solution)
기존에 실행 중인 터미널 백그라운드 태스크를 종료하거나, 필요할 시 포트 번호를 명시적으로 변경하여 실행합니다.
```bash
# 다른 포트 지정 실행 예시
PATH=$PATH:$(pwd)/node_modules/.bin hugo server --port=1314
```

---

## 4. 미지원 아이콘 경로 경고 (Warning)

### 문제 증상 (Symptom)
서버 실행 로그 창에 다수의 누락된 아이콘 경고가 출력됨:
```text
WARN HBX WARN: The icon `envelope` was not found in `assets/media/icons/solid/`.
WARN HBX WARN: The icon `heart` was not found in `assets/media/icons/solid/`...
```

### 원인 (Cause)
`content/_index.md` 세션에 아이콘 값을 입력할 때, 구버전 또는 다른 아이콘 라이브러리 형식인 `solid/heart`와 같이 경로형(Prefix)으로 지정한 것이 원인입니다. 최신 Hugo Blox 프레임워크는 Heroicon 이름 단어 단독으로만 수용하여 solid 폴더 내에서 아이콘을 매칭합니다.

### 해결 방법 (Solution)
`_index.md` 설정 파일에서 기존 아이콘 경로 앞의 `solid/` 접두사를 모두 제거하여 표준 형식으로 변경했습니다.
- `solid/users` ➔ `users`
- `solid/heart` ➔ `heart`
- `solid/music` ➔ `musical-note`
- `solid/palette` ➔ `paint-brush`
- `solid/bolt` ➔ `bolt`
- `solid/book-open` ➔ `book-open`

---

## 5. 원격 푸시 인증 오류 (fatal: could not read Username)

### 문제 증상 (Symptom)
원격 깃허브 저장소로 `git push`를 시도했을 때 터미널 푸시가 거부됨:
```text
fatal: could not read Username for 'https://github.com': Device not configured
```

### 원인 (Cause)
HTTPS 프로토콜의 특성상 원격 저장소에 쓰기 작업을 수행하기 위해서는 터미널 세션 상에서 GitHub 인증 정보(Username / Personal Access Token) 입력이 필수적이나, 자동화된 에이전트 터미널은 비대화형(Non-interactive) 모드로 동작하여 입력 장치를 마운트하지 못해 중단된 것입니다.

### 해결 방법 (Solution)
사용자가 직접 로컬 터미널(VS Code의 대화형 터미널)을 통해 `git push -u origin main`을 실행하여 운영체제(macOS) 키체인 또는 SSH Key 쌍을 통한 인증 절차를 거치도록 하였습니다.
