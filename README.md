# git_practice

---

## git 초기화 및 커밋

git 저장소를 초기화하고 커밋을 수행한다.

```bash
git init
git add README.md
git commit -m "first commit"
git branch -M main
```

- `git init`: 현재 디렉토리에 Git 저장소를 초기화한다.
- `git add README.md`: `README.md` 파일을 스테이징 영역에 추가한다.
- `git commit -m "first commit"`: 스테이징된 파일을 커밋한다.
- `git branch -M main`: 기본 브랜치 이름을 `main`으로 변경한다.

---

## 브랜치 생성

새로운 브랜치를 생성하고 파일을 추가한 후 원격 저장소에 푸시한다.

```bash
git checkout -b feature/header
echo "<h1>Header</h1>" > header.html
git add header.html
git commit -m "feat: add header section"
git push -u origin feature/header
```

- `git checkout -b feature/header`: `feature/header` 브랜치를 생성하고 전환한다.
- `echo "<h1>Header</h1>" > header.html`: `header.html` 파일을 생성한다.
- `git add header.html`: 파일을 스테이징 영역에 추가한다.
- `git commit -m "feat: add header section"`: 파일을 커밋한다.
- `git push -u origin feature/header`: 브랜치를 원격 저장소에 푸시하고 추적 관계를 설정한다.

---

## 파일 추가 및 커밋

추가적인 파일을 생성하고 커밋한다.

```bash
echo "function login() {}" > login.js
git add login.js
git commit -m "feat: implete basic login function"
echo "// fixed null reference" >> login.js
git commit -am "fix: handle null user object in login"
echo "<style>body { margin: 0; }</style>" > style.css
git add style.css
git commit -m "style: reset body margin"
```

---

## 원격 저장소와의 연동

원격 저장소를 추가하고 `main` 브랜치를 푸시한다.

```bash
git remote add origin https://github.com/dbwls99706/git_practice.git
git push -u origin main
```

- `git remote add origin <URL>`: 원격 저장소를 추가한다.
- `git push -u origin main`: `main` 브랜치를 푸시하고 추적 관계를 설정한다.
(이 작업을 수행하려면 settings의 developer settings에서 token을 생성하고 받아와야 한다.)

---

## 충돌 발생 및 해결 실습

`main` 브랜치와 `feature/conflict_test` 브랜치에서 동일한 파일을 수정하여 충돌을 발생시키고 해결한다.

```bash
git checkout main
echo -e "function login() {\n  console.log(\"login from main\");\n}" > login.js
git add login.js
git commit -m "feat: login function from main"

git checkout -b feature/conflict_test
echo -e "function login() {\n  console.log(\"login from feature branch\");\n}" > login.js
git add login.js
git commit -m "feat: login function from feature branch"

git merge main
```
위 명령어를 수행하면 경고가 뜬다.
이에 파일을 수정하여 충돌 부분을 제거한다.

충돌 해결 후:

```bash
git add login.js
git commit -m "merge: resolved conflict between main and feature branch"
```

---

## 로그 확인

커밋 히스토리를 그래프로 확인한다.

```bash
git log --oneline --graph --all
```

---

## 결론

이 실습을 통해 Git의 커밋과 브랜치의 개념, 사용법, 충돌 해결 방법을 체험해본다. 이러한 기술은 협업과 코드 관리에서 필수적이므로, 실무에서 적극 활용할 수 있다.
