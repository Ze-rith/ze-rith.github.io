# 🚓 사이버범죄수사대 수사관 로드맵 (Web)

8년·416주·1,053개의 투두로 만든 인터랙티브 로드맵.

**Live:** https://zerith.github.io/

---

## 📦 이게 뭐임?

- 원본 `roadmap.html` (PDF용)을 GitHub Pages용 **체크박스 투두 사이트**로 변환
- 체크 → 새로고침해도 유지 (`localStorage` 사용, 너의 브라우저에만 저장됨)
- 단계별·섹션별 진행률 자동 계산
- 검색 / 미완료만 보기 / 모두 펼치기 — 1,000개 넘어가도 안 헤맴
- 모바일에서도 잘 됨

---

## 🚀 zerith.github.io에 올리는 법

처음 GitHub Pages 쓰는 거라면:

### 1) `zerith.github.io` 리포 만들기
- GitHub 로그인 → New repository
- **이름은 정확히 `zerith.github.io`** (소문자, 너 아이디 = zerith)
- Public으로 만들기
- README 같은 거 체크하지 말고 비어있게 생성

### 2) `index.html` 업로드
- 만든 리포 페이지에서 **"uploading an existing file"** 클릭
- 이 폴더의 `index.html`을 끌어다 놓기
- 아래쪽 "Commit changes" 클릭

### 3) Pages 활성화
- 리포 → Settings → 좌측 메뉴 **Pages**
- Source: **Deploy from a branch**
- Branch: `main` / `/(root)` → Save
- 1~2분 후 https://zerith.github.io/ 에 접속

> ⚠️ 처음 만들면 DNS 반영에 5~10분 걸릴 수도 있음. 새로고침 ㄱㄱ

### git CLI 쓸 줄 알면 (소마고생이니 이쪽이 더 익숙할듯)
```bash
git clone https://github.com/zerith/zerith.github.io.git
cd zerith.github.io
# index.html 복사해서 넣기
git add index.html
git commit -m "init: cyber roadmap"
git push
```

---

## ✏️ 나중에 로드맵 수정하고 싶을 때

방법 A — **이 파일을 직접 수정**
- `index.html`을 열면 단계/주차/태스크가 다 들어있음
- 그냥 수정하고 push

방법 B — **원본 markdown/html에서 다시 생성**
- 원본 `roadmap.html`을 수정
- 같이 들어있는 `parse_roadmap.py` → `build_site.py`를 다시 돌리면 새 `index.html`이 나옴
- (이건 로컬에 Python + beautifulsoup4 깔려있어야 함: `pip install beautifulsoup4`)

---

## 💾 데이터 백업/이전

체크 상태는 **이 브라우저에만** 저장돼 있음. 다른 기기에서 이어서 하고 싶거나 백업하려면:

브라우저 콘솔(F12) 열고:
```js
// 백업 (복사해서 보관)
copy(localStorage.getItem("zerith-roadmap-v1"))

// 복원 (붙여넣을 때)
localStorage.setItem("zerith-roadmap-v1", '여기에 백업한거 붙여넣기')
```

---

## 🎨 색이 마음에 안 들면

`index.html` 상단의 `:root { ... }` 안에 모든 색이 CSS 변수로 정리돼있음.
- `--accent` (시안) → 메인 강조색
- `--gold` (골드) → 현재 주차 강조
- `--bg`, `--bg-2`, `--bg-3` → 배경 단계
- `--warn` → ⚠️ 색

---

## ⚡ 키 포인트

- **`section--current`** 클래스가 붙은 섹션이 "지금 이 주" → 지금은 W0
- 한 주가 지나면 `index.html`에서 `data-section="s1_sec0"`(W0) 클래스를 떼고, 다음 주에 붙이면 됨
- 또는 자동화: 매주 자동으로 currentWeek가 바뀌게 하려면 JS에서 날짜 계산 로직 추가 가능 (원하면 말해)

---

**8년 뒤의 너를 위해, 오늘 한 가지부터. 화이팅 💪**
