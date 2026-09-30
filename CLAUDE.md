# DASHBOARD PROJECT — Claude 작업 규칙

이 파일은 이 폴더에서 시작하는 Claude 세션에만 적용된다.
(2026-09-30 홈 메모리 `~/.claude/projects/.../memory/`에서 이전)

## 프로젝트 홈 (단일 원본)

- 로컬 작업 폴더는 **`E:\개발 PROJECT\DASHBOARD PROJECT`** 가 유일한 기준이다.
- `engineering-dashboard.html`이 소스 단일 원본. 운영 아티팩트와 GitHub `ghpages/index.html`은
  이 파일에서 생성된다 (`make_pages.py` 실행 → ghpages에서 commit/push).
- 과거 위치(D:\기술기획팀\... , Temp scratchpad)의 사본이 발견되면 **편집 금지** — 스테일 잔재다.
- 운영 아티팩트(id `dc10b060-5540-4c24-9b03-edeaece70495`) 재게시 시:
  file_path는 E:의 `engineering-dashboard.html`, `url` 파라미터로 기존 아티팩트를 지정한다
  (url 없이 게시하면 별도 아티팩트가 생긴다).

## files/ doc_id 규칙 (재발 사고 방지)

- 아티팩트 DB `files/` 컬렉션의 doc_id는 **원본 Excel의 full sha256 해시**다.
- 해시는 반드시 소스(seed JSON 또는 sha256sum 출력)에서 **전체 64자리를 읽어 그대로** 사용한다.
  축약된 prefix에서 뒷자리를 지어내는 실수가 2회 재발했다 — 절대 금지.
- files/ 쓰기 후에는 read_db로 `id == data.hash` 를 검증한다.
