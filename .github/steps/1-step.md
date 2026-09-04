## 1단계 · 보안 정책을 문서로 만든다

외부 연구자가 취약점을 찾았을 때 어디로 연락해야 하는지가 저장소에 적혀 있어야 합니다.

### 할 일

`SECURITY.md` 파일을 만들고 아래 두 제목을 반드시 포함하세요.

```markdown
# Security Policy

## Supported Versions
| 버전 | 지원 여부 |
| --- | --- |
| 1.x | 지원 |
| 0.x | 미지원 |

## Reporting a Vulnerability
비공개로 알려주세요. Security 탭의 Report a vulnerability 를 사용합니다.
공개 이슈로 올리지 마세요. 5영업일 안에 회신합니다.
```

### 왜 이렇게 하나

`SECURITY.md` 는 단순한 문서가 아닙니다. 이 파일이 있으면 저장소 Security 탭에
**Report a vulnerability** 버튼이 활성화되고, 비공개 신고 통로가 열립니다.

파일이 없으면 연구자는 공개 이슈로 취약점을 올립니다. 그 순간 취약점이 전 세계에 공개됩니다.
문서 한 장이 노출 시점을 바꿉니다.
