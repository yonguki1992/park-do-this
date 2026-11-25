# park-do-this
탱크도 잡고 원전도 막는데 코드 리팩토링쯤이야 — 이병 박현준 AI 에이전트 스킬

“박현준, 이 함수 리팩토링해!”라고 부르면 짧게 답하고 작업에 착수합니다. 코드, 주석, 커밋 메시지, PR 본문과 기술 문서에는 프로젝트의 기존 작성 규칙을 적용합니다.

## Claude Code 마켓플레이스 설치

Claude Code 대화창에서 아래 두 줄을 차례로 실행합니다.

```text
/plugin marketplace add yonguki1992/park-do-this
/plugin install park-hyun-jun@park-do-this
```

등록 명령의 일반형은 `/plugin marketplace add <OWNER>/<REPO>`입니다. 같은 이름의 플러그인이 하나뿐이면 `/plugin install park-hyun-jun`으로도 설치할 수 있습니다. 설치 후 새 세션에서 “박현준, 변경 사항 요약해줘”라고 입력합니다.

## 프로젝트에 수동 설치

이 저장소의 `plugins/park-hyun-jun/skills/park-hyun-jun/` 폴더를 통째로 복사합니다. 아래 경로는 스킬을 사용할 프로젝트 루트 기준입니다.

| 도구 | 복사 후 파일 위치 |
| --- | --- |
| Claude Code | `.claude/skills/park-hyun-jun/SKILL.md` |
| Codex | `.agents/skills/park-hyun-jun/SKILL.md` |
| Cursor | `.cursor/skills/park-hyun-jun/SKILL.md` |

예를 들어 이 저장소와 대상 프로젝트가 같은 상위 폴더에 있다면, 대상 프로젝트 루트에서 다음을 실행합니다. Codex나 Cursor에서는 첫 줄을 표의 해당 스킬 디렉터리로 바꿉니다.

```sh
skills_dir=.claude/skills
mkdir -p "$skills_dir"
cp -R ../park-do-this/plugins/park-hyun-jun/skills/park-hyun-jun "$skills_dir/"
```

## 사용 예시

**사용자**　박현준, 이 함수 리팩토링해!

**응답**　알겠습니다. 바로 처리한다.

에이전트가 함수를 수정하고 테스트를 실행한 뒤 보내는 보고 예시입니다.

```text
완료.
임무 — normalizeName의 중복 분기 정리
조치 — 입력 앞뒤 공백 제거를 한 곳으로 통합
검증 — 기존 단위 테스트 3개 통과
특이사항 — 없음
```

**사용자**　이병 박현준, 빈 문자열도 falsy야?

**응답**　네. JavaScript에서 빈 문자열은 falsy다.

## 패키지 검증

저장소 루트에서 Claude Code CLI로 두 매니페스트를 검사합니다.

```sh
claude plugin validate .
claude plugin validate ./plugins/park-hyun-jun
```

[Claude Code 마켓플레이스 명세](https://code.claude.com/docs/en/plugins/marketplace-reference) · [플러그인 매니페스트 명세](https://code.claude.com/docs/en/plugins/manifest-reference) · [MIT 라이선스](LICENSE)
