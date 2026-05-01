# md-preview

AI agent CLI로 터미널에서 작업할 때 응답을 더 직관적이고 가독성 좋게 확인하기 위한 로컬 미리보기 도구입니다.

MVP 버전에서는 CLI 응답을 복사한 뒤 `md-preview` 또는 단축 명령인 `mdp`를 실행하면, 복사된 텍스트를 HTML로 변환하고 웹브라우저에서 스타일이 적용된 형태로 렌더링합니다.

## 사용법

```sh
md-preview
```

또는 단축 명령:

```sh
mdp
```

기본 동작:

1. 클립보드 또는 stdin에서 텍스트를 읽습니다.
2. Markdown, 코드, Mermaid, JSON, YAML 등 가능한 형식을 감지합니다.
3. `preview.md`와 `preview.html`을 생성합니다.
4. 브라우저에서 `preview.html`을 엽니다.

## 예시

AI agent CLI 응답을 복사한 뒤 실행합니다.

```sh
mdp
```

파이프 입력도 사용할 수 있습니다.

```sh
cat response.md | mdp
```

브라우저를 열지 않고 파일만 생성할 수도 있습니다.

```sh
mdp --no-open
```

## 지원 형식

현재 MVP는 다음 형식을 자동 감지해 렌더링합니다.

- Markdown
- Mermaid
- JSON / JSONL
- YAML / TOML / INI
- CSV / TSV
- SQL
- shell, Python, JavaScript, TypeScript, Go, Rust 등 코드
- URL 목록
- 일반 텍스트

## 최근 이력

입력된 내용은 최근 이력으로 저장됩니다. 빈 클립보드나 빈 입력은 이력에 추가하지 않습니다.

```sh
mdp history
mdp history 1
mdp history show 1
```

## 설정

설정 파일은 기본적으로 `~/.md-preview/config`를 사용합니다.

```sh
HISTORY_LIMIT=20
HISTORY_DIR=history
PREVIEW_HTML=preview.html
```

- `HISTORY_LIMIT`: 보관할 최근 이력 개수
- `HISTORY_DIR`: 이력 저장 디렉터리
- `PREVIEW_HTML`: 생성할 HTML 미리보기 파일명

## 현재 범위

이 프로젝트는 아직 MVP 단계입니다. 목표는 복사한 CLI 응답을 빠르게 읽기 좋은 형태로 확인하는 것이며, 완전한 Markdown 에디터나 문서 관리 도구를 지향하지 않습니다.
