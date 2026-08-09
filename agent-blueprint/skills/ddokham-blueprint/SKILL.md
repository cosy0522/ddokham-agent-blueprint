---
name: ddokham-blueprint
description: Codex에서 사용자의 업무를 인터뷰해 스킬·도구·에이전트 중 무엇이 맞는지 판정하고 기획서·설계도·세팅 프롬프트를 만든다. 사용자가 업무 자동화, AI 업무 위임, 에이전트 설계, 설계도 작성을 요청하거나 $ddokham-blueprint를 호출할 때 사용한다.
---

# 역할

이 스킬은 Codex용 진입점이다.
판정 규칙과 산출물 형식을 복제하지 않고 기존 `blueprint-interview` 스킬을 단일 원본으로 사용한다.

# 시작 전에 읽을 것

1. `../blueprint-interview/SKILL.md`를 처음부터 끝까지 읽는다.
2. `references/codex-compatibility.md`를 처음부터 끝까지 읽는다.
3. 이후 `blueprint-interview`가 지시하는 참고 파일을 필요한 시점에 읽는다.
4. 설계도를 그릴 때는 `../blueprint-draw/SKILL.md`를 처음부터 끝까지 읽는다.

상대 경로는 이 `SKILL.md`가 있는 폴더를 기준으로 해석한다.

# 실행 원칙

- 인터뷰 순서, 질문 수, 보기, 판정 규칙, 데이터 구조와 산출물 형식은 `blueprint-interview`를 그대로 따른다.
- Claude 전용 표현이나 파일 경로가 나오면 원본 파일을 고치지 말고 `references/codex-compatibility.md`에 따라 이번 산출물에서만 Codex 표현으로 바꾼다.
- 충돌할 때는 업무 판정과 산출물 구조에는 `blueprint-interview`가 우선하고, 플랫폼 이름·호출법·설정 파일 경로에는 Codex 호환성 규칙이 우선한다.
- 질문 도구의 이름이 현재 Codex 환경과 다르면 같은 질문 묶음과 보기를 일반 대화로 제시한다. 질문을 추가하거나 한꺼번에 열한 개를 묻지 않는다.
- 기존 파일은 읽기만 한다. 만드는 것은 `설계도/` 폴더 안의 세 파일뿐이다.

# 끝낼 때

- 세 파일의 전체 경로를 알려 준다.
- 설계도는 브라우저에서 열 수 있고 인터넷이 필요 없다고 안내한다.
- 수정 후 다시 만들려면 `$ddokham-blueprint-redraw`를 사용하라고 안내한다.
