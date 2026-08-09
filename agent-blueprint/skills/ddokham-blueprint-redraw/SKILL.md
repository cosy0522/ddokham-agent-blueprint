---
name: ddokham-blueprint-redraw
description: Codex에서 사용자가 수정한 설계도/기획서.md를 기준으로 설계도 HTML과 세팅 프롬프트를 다시 만든다. 인터뷰 없이 기존 설계를 다시 그리거나 $ddokham-blueprint-redraw를 호출할 때 사용한다.
---

# 역할

이 스킬은 기존 Claude Code 재작성 커맨드의 Codex용 진입점이다.
기획서를 원본으로 삼아 설계도와 세팅 프롬프트만 다시 맞춘다.

# 시작 전에 읽을 것

1. `../../commands/ddokham-blueprint-redraw.md`를 처음부터 끝까지 읽는다.
2. `../ddokham-blueprint/references/codex-compatibility.md`를 처음부터 끝까지 읽는다.
3. `../blueprint-interview/SKILL.md`의 참고 파일 규칙을 확인한다.
4. 설계도를 그릴 때는 `../blueprint-draw/SKILL.md`를 처음부터 끝까지 읽는다.

상대 경로는 이 `SKILL.md`가 있는 폴더를 기준으로 해석한다.

# 실행 원칙

- 인터뷰를 다시 하지 않는다.
- `설계도/기획서.md`가 없으면 빈 파일을 만들지 말고 `$ddokham-blueprint`를 먼저 사용하라고 안내한다.
- 재작성 순서와 판정 규칙은 기존 커맨드를 따른다.
- Claude 전용 표현과 경로는 원본 파일을 고치지 말고 Codex 호환성 규칙에 따라 새 산출물에서만 바꾼다.
- 요청받지 않은 기획서 내용은 고치지 않는다.
- `설계도/` 밖의 파일은 수정하거나 삭제하지 않는다.

# 끝낼 때

- 바뀐 내용을 한두 줄로 요약한다.
- 다시 만든 파일의 전체 경로를 알려 준다.
- 설계도 HTML을 브라우저에서 다시 열어 확인하라고 안내한다.
