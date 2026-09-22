# Personal academic site

정적 HTML/CSS 두 개짜리 사이트입니다. 빌드 도구, npm, 프레임워크 없음 → GitHub Pages에 올리면 그대로 뜹니다.

```
index.html      내용 (여기를 고칩니다)
styles.css      디자인 (색/폭은 맨 위 :root 변수만)
assets/
  photo.jpg     프로필 사진 (선택)
```

## 1. 내용 채우기

`index.html`을 열면 `✏️` 와 `<!-- ... -->` 주석으로 구간이 나뉘어 있습니다. 바꿀 곳:

| 찾을 것 | 바꿀 것 |
|---|---|
| `Jongjin Baek` | 본인 이름 (5군데: title, meta, topbar, h1, 논문 저자) |
| `XXX` / `YYY` / `AAA` | 전공, 소속, 연구 주제 |
| `#` 링크 | 실제 PDF / arXiv / DOI / GitHub URL |

안 쓰는 섹션(Teaching, Awards, Projects…)은 `<section>` 또는 `<h2>` 블록을 통째로 지우고, 상단 `topbar__links`의 해당 링크도 같이 지우면 됩니다.

### 논문 추가하기

`<li class="pub">` 블록을 복사해서 붙이고 내용만 바꿉니다.
대표 논문은 `class="pub pub--selected"` 로 하면 왼쪽에 강조선이 생깁니다.
연도가 바뀌면 `<h3 class="year">2027</h3>` + 새 `<ol class="pubs">` 를 위에 추가합니다.

## 2. 색/폭 바꾸기

`styles.css` 맨 위 `:root` 블록만 건드리면 됩니다.

```css
--accent:  #1f5c9e;   /* 링크·강조선 색 */
--measure: 44rem;     /* 본문 폭. 넓히려면 48rem 등 */
```

다크모드는 브라우저 설정을 따라 자동으로 바뀝니다.

## 3. GitHub Pages 배포

1. GitHub에서 새 저장소를 만듭니다.
   - 주소를 `https://<아이디>.github.io` 로 쓰려면 저장소 이름을 정확히 `<아이디>.github.io`
   - 아니면 아무 이름이나 (주소가 `https://<아이디>.github.io/<저장소이름>/` 이 됩니다)
2. 이 폴더의 파일들을 저장소 루트에 올립니다 (`index.html`이 최상단이어야 합니다).
   ```bash
   git init
   git add .
   git commit -m "Add personal site"
   git branch -M main
   git remote add origin https://github.com/<아이디>/<저장소이름>.git
   git push -u origin main
   ```
3. 저장소 → **Settings → Pages** → Source를 **Deploy from a branch**, 브랜치 `main` / 폴더 `/ (root)` 로 지정 → Save.
4. 1~2분 뒤 주소가 나옵니다.

> 웹에서 드래그&드롭으로 파일을 업로드해도 똑같이 동작합니다 (git 몰라도 됩니다).

## 4. 배포 후 마무리

- `index.html`의 `og:url`, `og:image` 주석을 풀고 실제 주소를 넣으면 슬랙/트위터에 링크할 때 카드가 뜹니다.
- Google Scholar 프로필과 이메일 서명에 이 주소를 넣어두세요. 사이트는 링크가 걸려야 의미가 생깁니다.
- 논문이 추가될 때마다 `index.html`만 고쳐서 push하면 됩니다. Footer의 `Last updated`도 같이 고치세요.

## 5. 로컬에서 미리보기

`index.html`을 브라우저로 그냥 열어도 되고, 더 정확히 보려면:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

---

인쇄(`Cmd/Ctrl+P`)하면 내비게이션이 빠지고 CV 형태로 출력되도록 스타일이 들어 있습니다.
