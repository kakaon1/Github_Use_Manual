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
  
:: 기존의 저장소 때문에 문제가 생길시  
git remote remove origin  
git remote add origin https://github.com/계정명/Github_Use_Manual.git  
  
  
:: 업로드 시작(처음인 경우)  
echo "# Diablo_II_Resurrected_Multi" >> README.md  
git init  
git add README.md  
git commit -m "first commit"  
git branch -M main  
git remote add origin "유저레포지토리".git  
git push -u origin main  

:: 기존의 레포지토리가 있다면.
git remote add origin "유저레포지토리".git  
git branch -M main  
git push -u origin main  
  
:: 업로드 시작(처음이 아닌경우)  
git push  
  
:: git 레포지토리 초기화 방법  
git init  
git add .  
git commit -m 'initial commit'  
git remote add origin <깃헙 레포지토리 URL>  

# 한번 지웠다 다시 하면 에러가 발생한다. force push 명령어를 추가하여 강제 업로드 한다!  
git push origin master -f  
