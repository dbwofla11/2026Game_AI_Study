# 강의자료 — GitHub Pull Request(PR) 보내기

## 1. Pull Request란?

Pull Request(PR)는 내 브랜치의 변경 사항을 다른 브랜치에 반영해 달라고 요청하는 기능입니다. 이 스터디에서는 개인 브랜치에서 과제를 작성하고, `main` 브랜치로 PR을 보냅니다.

PR은 단순한 “제출 버튼”이 아니라 다음을 위한 협업 공간입니다.

- 변경 사항을 확인한다.
- 리뷰 의견을 주고받는다.
- 필요한 수정 사항을 반영한다.
- 승인된 변경을 안전하게 merge한다.

## 2. PR을 만들기 전 점검

GitHub에 push하기 전에 터미널에서 아래를 확인합니다.

```bash
git status
git branch --show-current
git log --oneline -3
```

확인할 내용은 다음과 같습니다.

- 현재 브랜치가 `lecture1/깃허브아이디`인가?
- 과제 파일이 커밋되었는가?
- `git status`에 커밋하지 않은 변경 사항이 없는가?
- 최신 커밋이 원격 저장소에 push되었는가?

## 3. GitHub에서 PR 만들기

1. GitHub에서 스터디 저장소 페이지로 이동합니다.
2. 브랜치를 push한 직후 보이는 **Compare & pull request** 버튼을 누릅니다.
   - 버튼이 보이지 않으면 상단 **Pull requests** → **New pull request**를 선택합니다.
3. 비교 대상 브랜치를 확인합니다.
   - **base**: `main` — 변경 사항이 들어갈 대상 브랜치
   - **compare**: `lecture1/깃허브아이디` — 내가 작업한 브랜치
4. 파일 변경 목록에서 본인의 제출 파일만 포함되었는지 확인합니다.
5. 아래 형식으로 제목과 본문을 작성합니다.
6. **Create pull request**를 눌러 생성합니다.

### PR 제목

```text
[Lecture1] 깃허브아이디
```

예시:

```text
[Lecture1] octocat
```

### PR 본문 템플릿

```md
## 작업 내용
- Lecture1 제출 파일을 추가했습니다.

## 확인 사항
- 파일 경로와 Markdown 렌더링을 확인했습니다.

## 질문 / 리뷰 요청
- 없음
```

## 4. PR 화면 읽는 법

| 탭 | 용도 |
| --- | --- |
| Conversation | 설명, 댓글, 승인 상태, CI 결과를 확인합니다. |
| Commits | PR에 포함된 커밋 목록을 봅니다. |
| Files changed | 실제로 변경된 파일과 줄 단위 차이를 확인합니다. |

PR을 열었을 때 가장 먼저 `Files changed` 탭을 봅니다. 의도하지 않은 파일, 개인 설정 파일, 대용량 파일이 포함되지 않았는지 확인하세요.

## 5. 리뷰 의견 반영하기

리뷰어가 수정 요청이나 질문을 남기면 같은 브랜치에서 수정합니다. 새 PR을 만들 필요가 없습니다.

```bash
# 파일 수정 후
git add Lecture1/submissions/깃허브아이디.md
git commit -m "docs: address Lecture1 review feedback"
git push
```

`git push`가 끝나면 기존 PR에 새 커밋이 자동으로 추가됩니다. PR 페이지에서 리뷰 댓글에 답글을 남기고, 수정한 내용을 간단히 알려 주세요.

```text
말씀해 주신 항목을 보완했습니다. 최신 커밋에서 확인 부탁드립니다.
```

## 6. 충돌(conflict)이 났을 때

PR에 “This branch has conflicts”가 표시되면, 다른 변경과 같은 부분을 수정했다는 뜻입니다. 당황해서 GitHub의 버튼으로 바로 해결하기보다 먼저 담당자에게 알려 주세요. 과제 제출에서는 다른 사람의 파일을 수정하지 않는다면 충돌이 드뭅니다.

직접 해결이 필요하다면 최신 `main`을 내 브랜치에 반영한 뒤 충돌 구간을 수정합니다.

```bash
git switch lecture1/깃허브아이디
git fetch origin
git merge origin/main
# 충돌 파일을 수정한 뒤
git add 충돌을해결한파일
git commit -m "merge: resolve conflicts with main"
git push
```

충돌 표시인 `<<<<<<<`, `=======`, `>>>>>>>`가 파일에 남지 않았는지 반드시 확인합니다.

## 7. Merge와 제출 완료

PR 생성만으로는 변경 사항이 `main`에 들어가지 않습니다. 리뷰와 승인 후 스터디 담당자가 merge합니다. 별도 안내가 없다면 제출자는 직접 merge하거나 PR을 닫지 않습니다.

merge된 뒤에는 로컬 `main`을 최신화할 수 있습니다.

```bash
git switch main
git pull origin main
```

## 8. PR 제출 체크리스트

- [ ] base 브랜치가 `main`이다.
- [ ] compare 브랜치가 내 `lecture1/깃허브아이디` 브랜치다.
- [ ] PR 제목이 `[Lecture1] 깃허브아이디` 형식이다.
- [ ] PR 본문에 작업 내용과 확인 사항을 적었다.
- [ ] `Files changed`에 의도한 파일만 있다.
- [ ] 리뷰 요청이 오면 같은 브랜치에 커밋하고 `git push`했다.
