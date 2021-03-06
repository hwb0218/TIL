```
얄팍한 코딩사전 Git 강좌 - 혼자작업편 (상)
```

## 왜 Git을 사용하나?

프로젝트를 진행하면 PC의 특정 폴더에 작업물들을 넣어놓는다.        
Git은 이 폴더안에 시간여행이 가능한 평행 우주를 만드는 것 인데           
시간여행이 가능하다는 것은 실수를 하거나, 어떠한 내용이 바뀌었는지 헷갈릴 때 과거로 돌릴 수 있다.      
또한 과거의 내용을 다른 과거나 현재로 가져올 수 있다.        
매번 폴더를 압축해서 시점별로 저장해 둘 필요가 없어진다는 것 이다.      
무언가를 만들고 싶은데 메인 작업에서 위험성이 발생할 수 있는 실험적인 부분을 시도한다거나      
다른 여러가지 버전 작업을 하고싶을 때 각각의 평행 우주에서 작업을 하고 기능이 마음에 들면     
현재 작업중인 우주로 가져올 수 있다.     

## Git 사용법
각 명령어는 터미널에 입력한다.     

1. Git 저장소 만들기

* git init - 비어있는 git 저장소를 생성한다.      
* git config --global user.name "(이름)" - 이름 등록      
* git config --global user.email "(내 메일주소)" - 이메일 등록   

2. 현재 시점을 저장하기

* git status - 파일의 상태를 확인
* git add -  타임캡슐에 넣음
* git commit -m "(내용)" - 타임캡슐을 묻는데 무엇인지 설명을 달아놓음
* git log - 이제까지의 묻은 타임캡슐 확인

3. 1 과거로 돌아가기 - Reset

* git reset 6자리 --hard - git log로 확인한 일련번호 6자리 입력 돌아간 시점 이후의 작업은 파괴됨

3. 2 과거로 돌아가기 - Revert

* git revert 6자리 - 돌아간 시점 이후의 작업이 파괴되지 않고 새 캡슐을 묻어놓음 

4. 평행우주 넘나들기 (동시에 다양한 작업을 할 수 있게 만들어 주는 기능) - Branch

* git branch - 브랜치 목록 전체를 확인
* git branch (branch 이름) - 브랜치 생성 / 현 시점에서 두 미래로 분기함 / 새로 생성한 브랜치에서 또 브랜치 생성이 가능함
* git checkout (branch 이름) - 브랜치 전환 / 생성한 브랜치는 마스터 브랜치 현 상태를 그대로 가져옴
* git checkout master - 마스터 브랜치로 전환

5.1 다른 우주에서 가져오기 (브랜치 병합하기) - merge

* git branch master - 마스터 브랜치로 전환
* git merge (branch 이름) - 브랜치의 변경 사항을 master 브랜치에 병합
* git log --graph --all --decorate - 시각화 된 분기 작업내용 보여줌 
