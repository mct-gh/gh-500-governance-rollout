## 4단계 · 상태를 API 로 확인한다

저장소가 300개면 화면을 300번 열 수 없습니다.

### 할 일

`scripts/audit.sh` 파일을 만들고 아래 내용을 넣으세요.

```bash
#!/usr/bin/env bash
# 저장소의 보안 기능 활성 상태를 한 줄로 뽑는다
set -euo pipefail
REPO="${1:-$GITHUB_REPOSITORY}"

gh api "repos/$REPO" --jq '
  .security_and_analysis
  | "secret_scanning=\(.secret_scanning.status) "
  + "push_protection=\(.secret_scanning_push_protection.status) "
  + "dependabot=\(.dependabot_security_updates.status)"
'

gh api "repos/$REPO/rulesets" --jq '.[] | "ruleset=\(.name) enforcement=\(.enforcement)"'
```

### 왜 이렇게 하나

`security_and_analysis` 는 저장소 객체 안에 들어 있습니다. 별도 엔드포인트가 아닙니다.
조직 전체를 볼 때는 `orgs/{org}/repos` 로 목록을 받아 같은 필드를 훑습니다.

시험은 "대규모로 보안 설정을 관리하는 방법"을 묻습니다. 답은 세 가지 층입니다.

1. 조직 수준 **보안 설정(security configurations)** 으로 기본값을 정한다
2. **룰셋**으로 규칙을 강제한다
3. **API** 로 실제 상태를 감사한다

화면에서 하나씩 켜는 것은 이 셋 중 어디에도 속하지 않습니다.
