:: 복사 붙여넣기 하는방법
Shift + Insert

:: git에 업로드 전 환경설정
git config --global user.name "계정명"
git config --global user.email "이메일"

:: 디렉토리 이동
cd test

:: git 레포지토리 올리기전 초기화하기
git init

:: git에 파일 업로드하기
:: 단일일 경우
git add First.txt

:: 전체 업로드인 경우
git add .

:: 주석이 필요한 경우
git commit -m "message"

:: 업로드 시작(처음인 경우)
echo "# Github_Use_Manual" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/유저명/Github_Use_Manual.git
git push -u origin main

:: 업로드 시작(처음이 아닌경우)
git push# Github_Use_Manual
# Github_Use_Manual
