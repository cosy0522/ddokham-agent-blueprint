# Codex에서 쓰는 법

이 플러그인은 기존 Claude Code용 파일을 유지하면서 Codex에서도 같은 업무 설계 절차를 실행한다.

## 설치

Codex CLI에서 GitHub 저장소를 마켓플레이스로 추가한다.

```powershell
codex plugin marketplace add Merciless-Hamster/ddokham-agent-blueprint --ref main
```

ChatGPT 데스크톱 앱을 다시 시작한 뒤 다음 순서로 설치한다.

1. Codex에서 **Plugins**를 연다.
2. `ddokham` 마켓플레이스를 선택한다.
3. `agent-blueprint`를 설치하고 활성화한다.
4. 새 작업을 시작한다.

저장소의 기존 `.claude-plugin/marketplace.json`은 Codex가 읽을 수 있는 레거시 호환 마켓플레이스이므로 별도 마켓플레이스 파일은 필요하지 않다.

## 사용

새 설계를 시작할 때:

```text
$ddokham-blueprint
```

`설계도/기획서.md`를 수정한 뒤 다시 그릴 때:

```text
$ddokham-blueprint-redraw
```

스킬 이름을 직접 쓰지 않아도 "내 업무를 자동화하고 싶다"처럼 요청하면 시작 스킬이 자동으로 선택될 수 있다.

## Claude Code와 함께 유지되는 구조

| 환경 | 시작 | 다시 그리기 | 매니페스트 |
|---|---|---|---|
| Claude Code | `/ddokham-blueprint` | `/ddokham-blueprint-redraw` | `.claude-plugin/plugin.json` |
| Codex | `$ddokham-blueprint` | `$ddokham-blueprint-redraw` | `.codex-plugin/plugin.json` |

기존 `commands/`, `skills/blueprint-interview/`, `skills/blueprint-draw/`, 템플릿과 참고 문서는 두 환경이 함께 사용하는 단일 원본이다.
Codex 전용 스킬은 원본을 복제하지 않고 호출 방식과 플랫폼 경로만 실행 중에 바꾼다.

## Codex 출력 경로

생성되는 세팅 프롬프트는 Codex 프로젝트 구조를 사용한다.

| 목적 | Codex 경로 |
|---|---|
| 프로젝트 지침 | `AGENTS.md` |
| 프로젝트 스킬 | `.agents/skills/{이름}/SKILL.md` |
| 사용자 정의 에이전트 | `.codex/agents/{이름}.toml` |

설계 단계에서는 위 파일을 실제로 만들지 않는다.
플러그인이 직접 만드는 것은 `설계도/` 안의 기획서, HTML 설계도, 세팅 프롬프트 세 파일뿐이다.

## 업데이트 테스트

플러그인을 수정한 뒤에는 새 작업에서 다음을 확인한다.

1. `$ddokham-blueprint`가 인터뷰를 시작하는지 확인한다.
2. 직접 호출하지 않아도 업무 자동화 요청에서 시작 스킬이 선택되는지 확인한다.
3. `설계도/` 밖의 기존 파일을 수정하지 않는지 확인한다.
4. 생성된 세팅 프롬프트가 `AGENTS.md`, `.agents/skills/`, `.codex/agents/`를 사용하는지 확인한다.
5. `$ddokham-blueprint-redraw`가 인터뷰 없이 두 파일을 다시 만드는지 확인한다.
