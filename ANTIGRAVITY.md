# AI4DT 설계도 — Google Antigravity

기존 Claude Code 플러그인 `agent-blueprint/`는 변경하지 않았습니다. Antigravity 전용 스킬은 `.agents/skills/`에 있습니다.

## 사용 방법

1. Antigravity에서 이 저장소(또는 `.agents/skills/` 내용을 복사한 작업 프로젝트)를 엽니다.
2. Agent 대화에서 `/ai4dt-blueprint`를 입력하거나 'AI4DT 설계 인터뷰 시작'이라고 요청합니다.
3. 질문에 답하면 현재 작업 폴더의 `설계도/`에 `기획서.md`, `설계도.html`, `세팅_프롬프트.md`가 생성됩니다.
4. `기획서.md`를 변경한 후 `/ai4dt-blueprint-redraw`를 입력하면 나머지 두 파일을 다시 생성합니다.

참고: 실제 슬래시 명령 노출 여부는 설치된 Antigravity 버전에 따라 다릅니다. 자동 발견되지 않으면 Agent에게 'ai4dt-blueprint 스킬을 사용해줘'라고 요청하세요.

## 주요 구성

- `ai4dt-blueprint/SKILL.md`: 11개 질문과 업무자동화 설계
- `ai4dt-blueprint/references/`: 원본의 질문·판정·출력 포맷을 그대로 복제
- `ai4dt-blueprint-redraw/SKILL.md`: 기획서 기반 재생성
- `blueprint-draw/SKILL.md`: HTML 렌더링 규칙
- `blueprint-draw/assets/blueprint-template.html`: 원본과 동일한 HTML 템플릿

## 안전 원칙

인터뷰와 재생성은 `설계도/` 이외 파일을 바꾸지 않습니다. 기존 결과물은 덮어쓰기 전에 확인하고, 민감정보나 문서의 실제 값은 설계도에 복사하지 않습니다. 실행/배포 등 실제 구현 작업은 별개입니다.

## 호환성

파일/스킬명은 플랫폼 간 인식 관례를 위해 소문자 `ai4dt-...`로 지정했습니다. 사용자 표시 브랜드는 **AI4DT**입니다.
