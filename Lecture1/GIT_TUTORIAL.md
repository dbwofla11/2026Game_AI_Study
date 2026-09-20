# Git 기초 튜토리얼

Git은 파일 변경 이력을 기록하고 여러 사람이 안전하게 함께 작업하도록 돕는 도구입니다. 이 문서는 과제를 제출하기 전까지 필요한 로컬 Git 작업 흐름을 다룹니다.

## 1. 처음 한 번만: Git 설치와 사용자 정보 설정

Git이 설치되어 있는지 확인합니다.

```bash
git --version
```

이름과 이메일을 설정합니다. 커밋 기록에 표시되므로 GitHub 계정의 이메일과 맞추는 것을 권장합니다.

```bash
git config --global user.name "홍길동"
git config --global user.email "you@example.com"
```

설정값은 아래 명령어로 확인합니다.

```bash
git config --global --list
```

## 2. 저장소 내려받기: `clone`

GitHub 저장소 페이지의 **Code** 버튼에서 HTTPS 주소를 복사한 뒤 실행합니다.

```bash
git clone https://github.com/조직이름/2026Game_AI_Study.git
cd 2026Game_AI_Study
```

`clone`은 원격 저장소를 내 컴퓨터에 복제하고, 해당 폴더를 Git 저장소로 준비합니다.

## 3. 현재 상태 확인: `status`

작업을 시작하거나 커밋하기 전에는 습관적으로 상태를 확인합니다.

```bash
git status
```

- **Changes not staged for commit**: 파일은 수정했지만 아직 커밋 후보로 선택하지 않은 상태입니다.
- **Changes to be committed**: `git add`로 스테이징하여 다음 커밋에 포함될 상태입니다.
- **working tree clean**: 저장하지 않은 변경 사항이 없습니다.

## 4. 작업 브랜치 만들기: `switch -c`

`main`에 직접 커밋하지 않습니다. 먼저 최신 상태를 받고 개인 브랜치를 만듭니다.

```bash
git switch main
git pull origin main
git switch -c lecture1/깃허브아이디
```

브랜치는 독립된 작업 공간입니다. 내 브랜치의 변경은 PR을 merge하기 전까지 `main`에 반영되지 않습니다.

현재 브랜치는 다음으로 확인합니다.

```bash
git branch --show-current
```

## 5. 변경 사항 선택: `add`

과제 파일을 만든 뒤 커밋에 넣을 파일만 스테이징합니다.

```bash
git add Lecture1/submissions/깃허브아이디.md
```

모든 변경 파일을 한꺼번에 추가하는 `git add .`도 있지만, 의도하지 않은 파일까지 포함될 수 있으므로 초반에는 파일 경로를 명시하는 방식을 권장합니다.

## 6. 변경 이력 저장: `commit`

스테이징한 변경 사항을 의미 있는 단위로 저장합니다.

```bash
git commit -m "docs: add Lecture1 submission for 깃허브아이디"
```

좋은 커밋 메시지는 “무엇을 바꿨는지”를 짧고 구체적으로 알려 줍니다.

```text
좋음: docs: add Lecture1 submission for octocat
피하기: 수정, 과제, asdf
```

최근 커밋은 다음 명령어로 확인할 수 있습니다.

```bash
git log --oneline -5
```

## 7. GitHub에 올리기: `push`

처음 push할 때는 로컬 브랜치와 원격 브랜치를 연결합니다.

```bash
git push -u origin lecture1/깃허브아이디
```

이후 같은 브랜치에서 추가 커밋을 올릴 때는 아래만 실행하면 됩니다.

```bash
git push
```

## 8. 과제용 전체 명령어 흐름

```bash
git clone https://github.com/조직이름/2026Game_AI_Study.git
cd 2026Game_AI_Study
git switch main
git pull origin main
git switch -c lecture1/깃허브아이디
# 제출 파일 작성
git status
git add Lecture1/submissions/깃허브아이디.md
git commit -m "docs: add Lecture1 submission for 깃허브아이디"
git push -u origin lecture1/깃허브아이디
```

이제 GitHub에서 PR을 만드는 방법은 [PR_LECTURE.md](PR_LECTURE.md)를 참고하세요.

## 자주 하는 실수

### `main`에서 작업을 시작했어요

아직 커밋하지 않았다면 새 브랜치를 바로 만들면 현재 변경 사항도 함께 이동합니다.

```bash
git switch -c lecture1/깃허브아이디
```

이미 `main`에서 커밋했다면 담당자에게 알려 주세요. 기록을 임의로 지우거나 강제로 push하지 않습니다.

### 실수로 다른 파일을 `git add`했어요

커밋 전이라면 스테이징에서만 제외할 수 있습니다.

```bash
git restore --staged 파일경로
```

### `push`할 때 인증 오류가 나요

GitHub HTTPS 인증에는 비밀번호 대신 브라우저 로그인 또는 Personal Access Token이 필요할 수 있습니다. 오류 메시지를 그대로 확인하고, 해결이 어렵다면 스터디 담당자에게 메시지와 함께 문의하세요.
