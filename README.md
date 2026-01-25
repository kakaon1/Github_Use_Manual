# Git 사용 매뉴얼 (Windows CMD)

## 복사 붙여넣기 방법
```bat
Shift + Insert
```

## Git 초기 환경설정 (최초 1회만)
```bat
git config --global user.name "계정명"
git config --global user.email "이메일"
```

## 디렉토리 이동
```bat
cd test
```

드라이브까지 바꿀 때:
```bat
cd /d C:\Users\Administrator\Desktop\go
```

## Git 저장소 초기화 (처음 1회만)
```bat
git init
```

## 파일 업로드하기

단일 파일:
```bat
git add First.txt
```

전체 업로드:
```bat
git add .
```

## 커밋 (주석 작성)
⚠️ CMD에서는 반드시 큰따옴표(") 사용!
```bat
git commit -m "message"
```

## 원격 저장소 관리

기존 저장소 때문에 문제가 생길 시:
```bat
git remote remove origin
git remote add origin https://github.com/계정명/레포명.git
```

URL만 변경 (더 안전):
```bat
git remote set-url origin https://github.com/계정명/레포명.git
```

## 처음 업로드 (README 생성)
```bat
echo "# 프로젝트명" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main
```

## 기존 레포지토리가 있을 때
```bat
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main
```

## 일반 업로드 (처음이 아닌 경우)
```bat
git push
```

## Git 레포지토리 초기화 방법
```bat
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main
```

## 강제 업로드 (Force Push)
⚠️ 주의: 원격을 덮어씀
```bat
git push -u origin main --force
```

## Push 거절 시 해결
원격이 더 최신인 경우:
```bat
git pull --rebase
git push
```

## 상위 폴더 .git 제거
꼬였을 때:
```bat
cd /d C:\Users\Administrator
rmdir /s /q .git
```

## 상태 확인
현재 Git 루트 확인:
```bat
git rev-parse --show-toplevel
```

상태 및 원격 확인:
```bat
git status
git remote -v
```

---

# 문제 발생 시 해결 방법

## 에러: "src refspec main does not match any"
원인: 커밋이 없거나 main 브랜치가 없음
```bat
git add .
git commit -m "init"
git branch -M main
git push -u origin main
```

## 에러: "remote origin already exists"
원인: 이미 origin이 등록되어 있음
```bat
git remote set-url origin https://github.com/계정명/레포명.git
```

## 에러: "Everything up-to-date"
원인: 커밋이 안되어 있어서 푸시할 내용이 없음
```bat
git add .
git commit -m "update"
git push
```

## 에러: "rejected (fetch first)"
원인: 원격 저장소가 로컬보다 최신 상태
```bat
git pull --rebase
git push
```

## 에러: "rejected (non-fast-forward)"
원인: 원격과 로컬의 히스토리가 달라서 병합 필요
```bat
git pull origin main
git push
```

## 에러: "pathspec 'commit'' did not match"
원인: CMD에서 작은따옴표(') 사용으로 인한 파싱 오류

❌ 잘못된 예시:
```bat
git commit -m 'initial commit'
```

✅ 올바른 예시:
```bat
git commit -m "initial commit"
```

## 에러: "fatal: The current branch main has no upstream branch"
원인: 업스트림(원격 추적) 설정이 안됨
```bat
git push --set-upstream origin main
```

또는:
```bat
git push -u origin main
```

## 문제: 상위 폴더가 Git 저장소로 잡힘
증상: AppData, Documents, NTUSER.DAT 등이 Untracked로 뜸

1. 현재 Git 루트 확인:
```bat
git rev-parse --show-toplevel
```

2. 결과가 `C:/Users/Administrator`로 나오면 상위 .git 삭제:
```bat
cd /d C:\Users\Administrator
rmdir /s /q .git
```

3. 다시 프로젝트 폴더에서 초기화:
```bat
cd /d C:\Users\Administrator\Desktop\go
git init
git add .
git commit -m "reinit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main --force
```

## 문제: 로컬 변경사항 무시하고 원격으로 덮어쓰기
```bat
git fetch origin
git reset --hard origin/main
```

## 문제: 충돌(Conflict) 발생 시
1. 충돌 파일을 직접 수정
2. 수정 후 추가 및 커밋:
```bat
git add .
git commit -m "Resolve conflicts"
git push
```

## 완전 초기화 (최후의 수단)
모든 게 꼬였을 때:
```bat
cd /d C:\Users\Administrator\Desktop\go
rmdir /s /q .git
git init
git add .
git commit -m "reinit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main --force
```
