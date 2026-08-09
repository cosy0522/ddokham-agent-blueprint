# Codex 호환성 규칙

이 파일은 기존 Claude Code용 원본을 바꾸지 않고 Codex에서 같은 설계 절차를 실행하기 위한 출력 어댑터다.

## 적용 범위

- 원본 `commands/`, `skills/`, `references/`, `assets/` 파일은 수정하지 않는다.
- 변환은 이번 실행에서 새로 만드는 `설계도/기획서.md`, `설계도/설계도.html`, `설계도/세팅_프롬프트.md`에만 적용한다.
- 사용자가 명시적으로 Claude Code용 결과를 요청하면 이 변환을 적용하지 않는다.
- 사용자가 플랫폼을 말하지 않으면 현재 실행 환경인 Codex를 대상으로 한다.

## 호출 방식

| 원본 표현 | Codex 표현 |
|---|---|
| `/ddokham-blueprint` | `$ddokham-blueprint` |
| `/ddokham-blueprint-redraw` | `$ddokham-blueprint-redraw` |
| Claude Code | Codex |
| Claude 계정에 올려두고 말로 시킨다 | Codex 플러그인 또는 스킬로 설치해 말로 시킨다 |

Claude 전용 질문 도구 이름이 나오면 현재 Codex 환경의 사용자 입력 기능을 사용한다.
전용 기능이 없으면 같은 단계의 2~3개 문항과 보기를 한 메시지에 묶어 일반 대화로 묻는다.

## 프로젝트 설정 파일

Codex용 세팅 프롬프트를 만들 때 다음 경로를 사용한다.

| Claude Code 경로 | Codex 경로 |
|---|---|
| `CLAUDE.md` | `AGENTS.md` |
| `.claude/skills/{이름}/SKILL.md` | `.agents/skills/{이름}/SKILL.md` |
| `.claude/agents/{이름}.md` | `.codex/agents/{이름}.toml` |

`AGENTS.md`가 이미 있으면 지우지 않는다.
기존 내용을 읽고 이어 적어도 되는지 사용자에게 확인한다.

Codex 사용자 정의 에이전트 파일은 TOML이며 최소한 다음 필드를 갖게 한다.

```toml
name = "agent_name"
description = "이 에이전트를 사용할 때"
developer_instructions = """
이 에이전트가 지킬 역할과 절차
"""
```

모델이나 추론 수준은 사용자가 요청하지 않으면 고정하지 않는다.

## 설계도 HTML

원본 `../blueprint-draw/assets/blueprint-template.html`은 수정하지 않는다.
먼저 `blueprint-draw` 절차대로 템플릿을 복사하고 데이터 블록을 넣는다.
그다음 생성된 `설계도/설계도.html` 복사본에서 Claude 전용 플랫폼 문구만 위 표의 Codex 표현으로 바꾼다.
화면 구성, 색, 글꼴, 레이아웃과 그리는 코드는 바꾸지 않는다.

이 플랫폼 문구 치환은 `blueprint-draw`의 "데이터 블록 밖을 건드리지 않는다" 규칙에 대한 유일한 Codex 예외다.

## 안전 범위

- 설계 단계에서는 `AGENTS.md`, `.agents/skills/`, `.codex/agents/`를 실제로 만들지 않는다.
- 위 경로는 `설계도/세팅_프롬프트.md` 안에 다음 단계의 대상으로만 적는다.
- 실제 세팅, 코드 작성, 초기화, 업로드는 하지 않는다.
- 기존 작업 파일은 수정하거나 삭제하지 않는다.
