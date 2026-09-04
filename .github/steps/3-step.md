## 3단계 · 룰셋으로 강제한다

이제 실제로 막을 차례입니다.

### 할 일

저장소 **Settings → Rules → Rulesets → New ruleset → New branch ruleset** 으로 들어갑니다.

1. 이름은 `protect-main` 으로 합니다
2. Enforcement status 를 **Active** 로 둡니다
3. Target branches 에 **Include default branch** 를 추가합니다
4. Rules 에서 아래를 켭니다
   - Require a pull request before merging
   - Require review from Code Owners
   - Require status checks to pass

만든 뒤 저장하세요. 채점기가 API 로 활성 룰셋이 있는지 확인합니다.

### 왜 이렇게 하나

룰셋은 브랜치 보호 규칙의 후속입니다. 차이가 시험에 나옵니다.

- 브랜치 보호는 저장소마다 따로 걸어야 합니다
- 룰셋은 **조직 수준에서 한 번에** 걸 수 있고, 여러 개가 겹쳐 적용됩니다
- 룰셋은 Evaluate 모드가 있어서, 막지 않고 **위반만 기록**해볼 수 있습니다

큰 조직에 새 정책을 넣을 때는 Active 로 바로 가지 않습니다.
Evaluate 로 몇 주 돌려 얼마나 깨지는지 보고 나서 Active 로 올립니다.
