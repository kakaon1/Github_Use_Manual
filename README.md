:: ============================================================
:: Git 사용 매뉴얼 (Windows CMD) - 완전판
:: ============================================================

:: [복사/붙여넣기]
:: Shift + Insert

:: ------------------------------------------------------------
:: 초기 설정 (최초 1회만)
:: ------------------------------------------------------------
git config --global user.name "계정명"
git config --global user.email "이메일"
git config --global core.autocrlf true
git config --global init.defaultBranch main
git config --global --list

:: ------------------------------------------------------------
:: 디렉토리 이동
:: ------------------------------------------------------------
cd /d C:\Users\Administrator\Desktop\go

:: ------------------------------------------------------------
:: 상태 확인 명령어
:: ------------------------------------------------------------
git status
git log
git log --oneline
git log --graph --oneline --all
git remote -v
git branch
git branch -a
git rev-parse --show-toplevel

:: ------------------------------------------------------------
:: 저장소 시작 (처음 1회만)
:: ------------------------------------------------------------
git init
git branch -M main

:: ------------------------------------------------------------
:: 원격 저장소 관리
:: ------------------------------------------------------------
git remote add origin https://github.com/계정명/레포명.git
git remote set-url origin https://github.com/계정명/레포명.git
git remote remove origin
git remote -v

:: ------------------------------------------------------------
:: 파일 추가/제거
:: ------------------------------------------------------------
git add .
git add 파일명.txt
git add *.js
git rm 파일명.txt
git rm --cached 파일명.txt

:: ------------------------------------------------------------
:: 커밋
:: ------------------------------------------------------------
git commit -m "메시지"
git commit -am "add와 commit 동시에"
git commit --amend -m "마지막 커밋 메시지 수정"

:: ------------------------------------------------------------
:: 처음 업로드 (README 포함)
:: ------------------------------------------------------------
echo "# 프로젝트명" >> README.md
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main

:: ------------------------------------------------------------
:: 처음 업로드 (기존 파일 전체)
:: ------------------------------------------------------------
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main

:: ------------------------------------------------------------
:: 일반 업로드 (추가/수정 후)
:: ------------------------------------------------------------
git add .
git commit -m "update"
git push

:: ------------------------------------------------------------
:: Push 거절 해결
:: ------------------------------------------------------------
git pull --rebase
git push

git pull origin main
git push

:: ------------------------------------------------------------
:: 강제 Push (주의: 원격 덮어씀)
:: ------------------------------------------------------------
git push -u origin main --force
git push --force-with-lease

:: ------------------------------------------------------------
:: Pull (원격에서 최신 받기)
:: ------------------------------------------------------------
git pull
git pull origin main
git pull --rebase

:: ------------------------------------------------------------
:: Fetch (받기만 하고 병합 안함)
:: ------------------------------------------------------------
git fetch
git fetch origin
git fetch --all

:: ------------------------------------------------------------
:: 로컬 변경사항 무시하고 원격으로 덮어쓰기
:: ------------------------------------------------------------
git fetch
git reset --hard origin/main

:: ------------------------------------------------------------
:: 변경사항 취소
:: ------------------------------------------------------------
git checkout -- 파일명.txt
git restore 파일명.txt
git restore .
git reset HEAD 파일명.txt
git reset --hard HEAD

:: ------------------------------------------------------------
:: 커밋 취소
:: ------------------------------------------------------------
git reset HEAD~1
git reset --soft HEAD~1
git reset --hard HEAD~1

:: ------------------------------------------------------------
:: Stash (임시 저장)
:: ------------------------------------------------------------
git stash
git stash save "작업 중"
git stash list
git stash apply
git stash pop
git stash drop
git stash clear

:: ------------------------------------------------------------
:: 브랜치 관리
:: ------------------------------------------------------------
git branch
git branch 브랜치명
git branch -M main
git branch -d 브랜치명
git branch -D 브랜치명
git checkout 브랜치명
git checkout -b 새브랜치명
git switch 브랜치명
git switch -c 새브랜치명
git merge 브랜치명

:: ------------------------------------------------------------
:: 특정 파일만 이전 버전으로 복구
:: ------------------------------------------------------------
git checkout 커밋해시 -- 파일명.txt
git restore --source=커밋해시 파일명.txt

:: ------------------------------------------------------------
:: 원격 브랜치 삭제
:: ------------------------------------------------------------
git push origin --delete 브랜치명

:: ------------------------------------------------------------
:: .gitignore 적용 (이미 추적된 파일 제거)
:: ------------------------------------------------------------
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"

:: ------------------------------------------------------------
:: 태그 관리
:: ------------------------------------------------------------
git tag
git tag v1.0.0
git tag -a v1.0.0 -m "버전 1.0.0"
git push origin v1.0.0
git push origin --tags

:: ------------------------------------------------------------
:: 충돌 해결 후
:: ------------------------------------------------------------
git add .
git commit -m "Resolve conflicts"
git push

:: ------------------------------------------------------------
:: 클론 (저장소 복제)
:: ------------------------------------------------------------
git clone https://github.com/계정명/레포명.git
git clone https://github.com/계정명/레포명.git 폴더명

:: ------------------------------------------------------------
:: 서브모듈
:: ------------------------------------------------------------
git submodule add https://github.com/계정명/레포명.git 경로
git submodule update --init --recursive

:: ------------------------------------------------------------
:: 잘못된 Git 저장소 제거 (상위 폴더 오염 시)
:: ------------------------------------------------------------
cd /d C:\Users\Administrator
rmdir /s /q .git

:: ------------------------------------------------------------
:: 에러별 해결법
:: ------------------------------------------------------------

:: src refspec main does not match any
git add .
git commit -m "init"
git branch -M main
git push -u origin main

:: remote origin already exists
git remote set-url origin https://github.com/계정명/레포명.git

:: Everything up-to-date (커밋 안됨)
git add .
git commit -m "update"
git push

:: rejected (fetch first)
git pull --rebase
git push

:: rejected (non-fast-forward)
git pull origin main
git push

:: pathspec 'commit'' did not match (따옴표 문제)
git commit -m "message"

:: ------------------------------------------------------------
:: 유용한 조합 명령어
:: ------------------------------------------------------------

:: 현재 상태 전체 확인
git status && git log --oneline -5 && git remote -v

:: 강제 초기화 (로컬을 원격과 완전 동기화)
git fetch origin
git reset --hard origin/main
git clean -fd

:: 빠른 업로드
git add . && git commit -m "update" && git push

:: 커밋 메시지 없이 빠른 커밋
git commit -am "quick update" && git push

:: ------------------------------------------------------------
:: 고급 명령어
:: ------------------------------------------------------------

:: 특정 커밋으로 되돌리기
git revert 커밋해시

:: 커밋 합치기 (squash)
git rebase -i HEAD~3

:: 커밋 히스토리 정리
git log --pretty=format:"%h %s" --graph

:: 변경된 파일만 보기
git diff
git diff --name-only
git diff HEAD

:: 누가 수정했는지 확인
git blame 파일명.txt

:: 파일 이동/이름 변경
git mv 이전파일명 새파일명

:: ------------------------------------------------------------
:: 자주 쓰는 워크플로우
:: ------------------------------------------------------------

:: [1] 처음 시작
cd /d C:\Users\Administrator\Desktop\프로젝트
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main

:: [2] 일상 업로드
cd /d C:\Users\Administrator\Desktop\프로젝트
git add .
git commit -m "update"
git push

:: [3] Pull 후 Push
git pull --rebase
git add .
git commit -m "update after pull"
git push

:: [4] 완전 초기화 후 재시작
cd /d C:\Users\Administrator\Desktop\프로젝트
rmdir /s /q .git
git init
git add .
git commit -m "reinit"
git branch -M main
git remote add origin https://github.com/계정명/레포명.git
git push -u origin main --force

:: [5] 원격 최신으로 로컬 덮어쓰기
git fetch origin
git reset --hard origin/main

:: ------------------------------------------------------------
:: 끝
:: ------------------------------------------------------------
