## Git Commit rule

### 제목

- 커밋 메시지 제목은 docs: Edit README.md to include New Features Use-Cases 와 같이 작성한다.

- 제목은 타입 라벨을 맨 앞에 붙어 타입(Type): 제목 형식으로 작성한다. 각 타입 라벨은 아래와 같다.

```
feat: 새로운 기능을 추가할 경우
fix: 버그를 고친 경우
docs: 문서 수정한 경우
style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
refactor: 프로덕션 코드 리팩터링
test: 테스트 추가, 테스트 리팩터링 (프로덕션 코드 변경 없음)
chore: 빌드 테스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)
```

- 제목의 처음은 동사 원형으로 시작하고 첫 글자는 대문자로 작성한다.
  "Fixed", "Added", "Changed" 등 과거 시제가 아닌 "Fix", "Add", "Change"로 명령어로 시작한다.
  총 글자 수는 50자 이내며 마지막에 마침표(.)를 붙이지 않는다.

### 본문 (선택)

- 본문은 커밋의 상세 내용을 작성한다. 제목과 본문 사이에 한 줄 비운다. 본문은 한 줄에 72자 이내로 작성한다. 한 줄을 띄워 문단으로 나누거나 불렛을 사용해 내용을 구분한다.

### 꼬리말 (선택)

- 꼬리말에는 이슈 트래커 ID를 추가한다.

### Example

```
feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequenses of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Typically a hyphen or asterisk is used for the bullet, preceded
  by a single space, with blank lines in between, but conventions
  vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```
