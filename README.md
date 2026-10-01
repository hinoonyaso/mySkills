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

## AI Agent 용어 적용 범위

이 저장소는 아래 개념을 별도 Skill로 늘리지 않고 기존 7개 작업 절차에 녹입니다.

| 개념 | 이 구성에서의 적용 |
| --- | --- |
| Prompt Engineering | 공용 지침과 작업별 Skill로 역할·규칙·완료 기준을 안내 |
| Context / Retrieval Engineering | 현재 프로젝트와 버전에 맞는 코드·문서만 선택하고 출처를 확인 |
| Memory Engineering | 구현 결정과 재사용 가치가 검증된 해결 경험을 프로젝트 문서에 기록 |
| Tool Engineering / MCP | 필요한 최소 도구만 쓰고 외부 데이터와 도구 권한을 검증 |
| Harness Engineering / Scaffolding | 저장소 지침, 실행 환경, 검증 명령, 권한과 피드백을 연결 |
| Workflow / Loop / Trajectory / State | 과제에 맞게 순서를 정하고, 실패에서 새 근거를 얻어 반복하며 진행 상태를 유지 |
| Evaluation / Observability | 완료 기준, 명령·조건·결과를 기록하고 검증 상태를 근거와 함께 보고 |
| Guardrail / Governance | 비밀 정보, 권한, 파괴적 변경과 사용자 결정의 경계를 지킴 |
| Inference Engineering | 모델 실행 성능이 핵심인 Edge AI 작업에서만 적용 |

MCP 연동이나 모델 추론 최적화는 해당 기술이 실제 과제에 필요할 때만 사용합니다. 문서상 절차와 현재 실행 환경의 기능을 구분하고, 도구·검증 기능을 사용할 수 없으면 그 제한을 보고합니다.

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

## 구현 근거와 해결 경험 기록

중요한 구현 결정은 선택한 방식, 고려한 대안, 선택 이유, 그 이유를 뒷받침하는 근거, 가정과 절충점, 검증 결과를 프로젝트 문서에 기록합니다. 근거에는 요구사항, 기존 동작, 버전이 확인된 공식 문서, 측정이나 테스트 결과 등이 포함됩니다. 프로젝트의 기존 ADR·설계 문서를 우선 사용하고, 장기 영향이 있는 결정에만 간결한 기록을 추가합니다.

오류 해결은 원인이 확인되고 재사용 가치가 있을 때 증상, 원인, 선택한 수정과 이유, 근거, 검증 및 재발 방지를 남깁니다. 일회성 실패와 민감 정보는 기록하지 않습니다. 여러 프로젝트에 공통인 교훈은 검증 후 Skill 개선 후보로 제안합니다.

## 관리 원칙

- Skill 이름은 폴더명 및 frontmatter의 `name`과 일치시킵니다.
- Codex와 Claude Code에 배포하는 동일 Skill의 `SKILL.md` 내용은 이 저장소의 파일을 기준으로 맞춥니다.
- 저장소별 지침과 환경에 맞게 필요한 Skill만 적용하고, 일반 지침과 중복되는 불필요한 절차는 추가하지 않습니다.
