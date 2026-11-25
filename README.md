# park-do-this

> **전차도 잡고 원전도 막는데 코드 리팩토링쯤이야 — 이병 박현준 AI 에이전트 스킬**

<p align="center"><img src="./assets/park-thumbs-up.jpeg" alt="이병 박현준" width="480" /></p>

그냥 빨리 전역하고 집 가고 싶은 대한민국 해병대 이등병이지만, **"박현준, 이거 해!"** 한 마디면 불평 없이 투입되어 레거시 코드부터 테스트 실패까지 단신으로 정리합니다.

* **사족 제로:** *"좋은 질문입니다! 기꺼이 도와드리겠습니다!"* 같은 쓸데없는 인사말 없이 바로 착수합니다.
* **산출물 분리 (중요):** 대화와 보고만 박현준 말투로 합니다. 실제 작성하는 **소스 코드, 주석, 커밋 메시지, PR 본문, 기술 문서**에는 군대 말투를 절대 섞지 않고 기존 프로젝트 컨벤션을 따릅니다.

---

## 소집 명령 (Claude Code 마켓플레이스 설치)

Claude Code 대화창에서 아래 두 줄을 차례로 입력해 박현준 이병을 배치합니다.

```text
/plugin marketplace add yonguki1992/park-do-this
/plugin install park-hyun-jun@park-do-this
```

등록 명령의 일반형은 `/plugin marketplace add <OWNER>/<REPO>`입니다. 같은 이름의 플러그인이 하나뿐이면 `/plugin install park-hyun-jun`으로도 설치할 수 있습니다. 설치 후 새 세션에서 **"박현준, 변경 사항 요약해줘"**라고 불러보세요.

## 수동 배치 (프로젝트 직접 설치)

마켓플레이스 없이 쓰거나 Codex, Cursor 등에 투입하려면 이 저장소의 `plugins/park-hyun-jun/skills/park-hyun-jun/` 폴더를 통째로 복사합니다. 아래 경로는 스킬을 사용할 프로젝트 루트 기준입니다.

| 도구 | 배치 위치 |
| --- | --- |
| Claude Code | `.claude/skills/park-hyun-jun/SKILL.md` |
| Codex | `.agents/skills/park-hyun-jun/SKILL.md` |
| Cursor | `.cursor/skills/park-hyun-jun/SKILL.md` |

이 저장소와 대상 프로젝트가 같은 상위 폴더에 있다면, 대상 프로젝트 루트에서 아래 명령을 실행합니다. (Codex나 Cursor에서는 첫 줄만 표의 경로로 변경)

```sh
skills_dir=.claude/skills
mkdir -p "$skills_dir"
cp -R ../park-do-this/plugins/park-hyun-jun/skills/park-hyun-jun "$skills_dir/"
```

---

## 작전 수행 예시

단순 수령은 `"알겠습니다."` 또는 `"네, 알겠습니다."`로 짧게 끊습니다.

**1. 무리한 작업 지시 (행동 선언 + 완료 보고)**

> **지휘관:** 박현준, 이 스파게티 함수 리팩토링해!
>
> **박현준:** 알겠습니다. 리팩토링 수행한다!

```text
완료했습니다.
- 임무: normalizeName 중복 분기 정리
- 조치: 입력 앞뒤 공백을 한 곳에서 제거하도록 수정했습니다.
- 검증: 기존 단위 테스트 3개 모두 통과했습니다.
- 특이사항: 없음
```

**2. 단순 질문**

> **지휘관:** 이병 박현준, 빈 문자열도 falsy야?
>
> **박현준:** 네. JavaScript에서 빈 문자열은 falsy입니다.

**3. 교전 중 (오류 복구)**

> 에러 확인(TypeError). null 체크 보강 후 재시도한다.

---

## 군기 점검 (패키지 검증)

저장소 루트에서 Claude Code CLI로 매니페스트 이상 유무를 확인합니다.

```sh
claude plugin validate .
claude plugin validate ./plugins/park-hyun-jun
```

[Claude Code 마켓플레이스 명세](https://code.claude.com/docs/en/plugins/marketplace-reference) · [플러그인 매니페스트 명세](https://code.claude.com/docs/en/plugins/manifest-reference) · [MIT 라이선스](LICENSE)