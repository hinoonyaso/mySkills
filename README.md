# mySkills

개발 아이디어를 실행 가능한 설계로 다듬고, 구현부터 검증과 운영까지 이어가기 위한 공용 Engineering Skills 모음입니다. Codex와 Claude Code에서 공통으로 사용할 수 있도록 각 Skill은 표준 `SKILL.md` 파일로 관리합니다.

## 포함된 Skills

| Skill | 용도 |
| --- | --- |
| `architecture-planning` | 아이디어와 요구사항을 정리하고 대안·절충점을 검토해 구현 방향을 추천 |
| `coding` | 기존 관례를 따르며 기능과 수정 사항을 구현 |
| `debugging` | 증상을 재현하고 근거를 통해 원인을 찾아 수정 |
| `testing-validation` | 기능·시스템이 완료 기준을 만족하는지 확인하고 결과를 기록 |
| `review-evaluation` | 코드, 설계, 구현 방식의 품질과 위험을 검토 |
| `security-review` | 코드와 시스템의 보안 위험, 권한, 신뢰 경계를 검토 |
| `deployment-operations` | 배포 준비와 운영, 상태 확인, 복구 절차를 다룸 |

작업 목적에 필요한 Skill만 선택합니다. 복합 작업에서는 예를 들어 신규 기능은 `architecture-planning → coding → testing-validation`, 버그 수정은 `debugging → coding → testing-validation` 순서로 연결할 수 있습니다.

## 저장소 구조

```text
skills/
├── architecture-planning/SKILL.md
├── coding/SKILL.md
├── debugging/SKILL.md
├── testing-validation/SKILL.md
├── review-evaluation/SKILL.md
├── security-review/SKILL.md
└── deployment-operations/SKILL.md
```

## 프로젝트에서 사용하기

필요한 Skill 디렉터리를 프로젝트에 복사합니다.

Codex 프로젝트:

```bash
mkdir -p .agents/skills
cp -r /path/to/mySkills/skills/<skill-name> .agents/skills/
```

Claude Code 프로젝트:

```bash
mkdir -p .claude/skills
cp -r /path/to/mySkills/skills/<skill-name> .claude/skills/
```

여러 Skill을 사용할 때는 필요한 디렉터리마다 복사 명령을 실행합니다. `<skill-name>`은 위 목록의 이름으로 바꿉니다. 예를 들어 `coding`을 적용하려면 `skills/coding` 디렉터리를 복사합니다.

## 관리 원칙

- Skill 이름은 폴더명 및 frontmatter의 `name`과 일치시킵니다.
- Codex와 Claude Code에 배포하는 동일 Skill의 `SKILL.md` 내용은 이 저장소의 파일을 기준으로 맞춥니다.
- 저장소별 지침과 환경에 맞게 필요한 Skill만 적용하고, 일반 지침과 중복되는 불필요한 절차는 추가하지 않습니다.
