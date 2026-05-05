# GitHub 업로드 가이드

이 폴더(`intergrated_care`)를 `https://github.com/at-korea/intergrated_care` 저장소로 올리는 단계입니다. 모두 Windows에서 실행하면 됩니다.

## 1단계 — GitHub에서 빈 저장소 만들기

1. https://github.com/new 접속 (`at-korea` 계정으로 로그인)
2. **Repository name**: `intergrated_care` (또는 `integrated-care` 같이 오타 수정도 가능)
3. **Public** 선택 (GitHub Pages 무료 기능을 위해)
4. **README, .gitignore, license 추가는 모두 체크 해제** (이미 로컬에 준비되어 있음)
5. **"Create repository"** 클릭

저장소가 비어 있는 화면에서 보이는 명령어 중 **"…or push an existing repository from the command line"** 섹션을 참고합니다 (아래 3단계와 거의 같음).

## 2단계 — 명령 프롬프트(또는 PowerShell) 열기

Windows에서 `Win + R` → `cmd` 입력 → 엔터.

또는 작업 폴더에서 주소창에 `cmd` 입력 후 엔터로 해당 폴더에서 바로 cmd 열기.

## 3단계 — 폴더로 이동 후 git 초기화

```cmd
cd "C:\Users\nrc\OneDrive\문서\96. claude_cowork_carerobot\17. 한국인데이터셋\1. 전국통합돌봄현황\intergrated_care"

git init -b main
git add .
git commit -m "Initial commit: 전국 통합돌봄서비스 대시보드"
git remote add origin https://github.com/at-korea/intergrated_care.git
git push -u origin main
```

> `git push` 시 GitHub 로그인 창이 뜹니다 — 브라우저에서 인증하거나 personal access token으로 인증하면 됩니다. (비밀번호 직접 입력은 더 이상 지원하지 않음)

## 4단계 — GitHub Pages 활성화

1. 저장소 페이지 → **Settings** 탭
2. 왼쪽 사이드바에서 **Pages** 클릭
3. **Source**: `Deploy from a branch`
4. **Branch**: `main` 선택, 폴더는 `/ (root)`
5. **Save** 클릭
6. 1~2분 기다리면 다음 URL에서 접속 가능:

```
https://at-korea.github.io/intergrated_care/
```

## 5단계 — 동작 확인

- `https://at-korea.github.io/intergrated_care/` → 랜딩 페이지(`index.html`)
- `https://at-korea.github.io/intergrated_care/dashboard.html` → 메인 통합 대시보드
- `https://at-korea.github.io/intergrated_care/search.html` → 검색 전용
- `https://at-korea.github.io/intergrated_care/analysis.html` → 심층 분석

## 이후 업데이트하는 방법

파일 수정 후:

```cmd
cd "C:\Users\nrc\OneDrive\문서\96. claude_cowork_carerobot\17. 한국인데이터셋\1. 전국통합돌봄현황\intergrated_care"
git add .
git commit -m "수정 내용 설명"
git push
```

## 주의 사항

- **OneDrive 폴더**에서 git을 사용하면 동기화 충돌 가능성이 있습니다. 가능하면 OneDrive 외 폴더(예: `C:\Users\nrc\Documents\GitHub\`)로 옮긴 후 git을 운영하는 것을 권장합니다.
- **파일 크기**: `dashboard.html` 4.9MB · `services_national.json` 4.5MB — GitHub 100MB 제한 이내. 문제 없음.
- **git이 설치되어 있지 않다면**: https://git-scm.com/download/win 에서 설치 후 진행.

## 문제 해결

### "Permission denied" 에러
GitHub 인증 실패. https://github.com/settings/tokens 에서 personal access token을 생성한 후, push 시 비밀번호 자리에 그 토큰을 붙여넣으세요.

### "remote: Repository not found"
저장소 이름이 다릅니다. `intergrated_care`로 만들었는지 확인하거나, 저장소 이름이 다르면 다음 명령으로 수정:
```cmd
git remote set-url origin https://github.com/at-korea/[실제이름].git
```

### Pages가 안 보임
Settings → Pages에서 활성화 후 1~5분 정도 빌드 시간이 필요합니다. Actions 탭에서 빌드 진행상황 확인 가능.
