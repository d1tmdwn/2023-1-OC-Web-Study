< git 명령어 정리 >
- git add: 변경된 파일을 staging area에 추가하는 명령어다. 변경된 파일들 중 commit하고자 하는 파일만 staging area에 추가할 수 있다.
- git commit: staging area에 추가된 파일들을 commit하여 local repository에 저장하는 명령어다.
- git push: local repository에 저장된 변경 내용을 remote repository에 반영하는 명령어다.
- git pull: remote repository에서 최신 변경 내용을 가져와 local repository에 반영하는 명령어다. 가져온 최신 변경 내용을 local repository에 합치는 작업까지 자동으로 수행된다.
- git fetch: remote repository에서 최신 변경 내용을 가져오지만, local repository에는 반영하지 않는 명령어다. 가져온 최신 변경 내용은 local repository와 합치기 전에 local repository에 합치는 작업을 따로 수행해야 한다.
** git pull과 fetch의 차의점: git pull은 remote repository와 local repository를 자동으로 동기화하고 최신 변경 내용을 local repository에 반영하는 명령어이며, git fetch는 remote repository에서 최신 변경 내용을 가져오기만 하고 local repository에는 반영하지 않는 명령어다.

< 1, 2 주차 강의 내용 정리 >

URI(Uniform Resource Identifier): URL(UR Location), URN(UR Name) - 리소스를 식별하는 통일된 방식
URL: 프로토콜 + DNS 주소 - 리소스가 있는 주소
DNS(Domain Name System) 주소: 길고 복잡한 IP주소들을 인간이 외우기에는 너무 길고, 관리하기도 너무 힘들다. 또한 아이피 주소는 사정에 따라 바뀔 수도 있다. -> DNS 서버를 통해 해결
리소스: HTML(자료-뼈대) + CSS(UI-살과 옷) + JavaScript(제어)
'이 리소스들을 재료 삼아 브라우저가 그림을 그린다(랜더링)' - 수업 중

먼저 'git'의 정의는 컴퓨터 파일의 변경사항을 추적하고 여려 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 '스냅샷 스트림' 기반의 '분산 버전 관리 시스템'이다. 
쉽게 말하자면, 파일의 변경 사항을 추적하고 협업 작업을 조율하게 해주는 것이다.
이는 Branch 라는 git의 특징을 통해 구현하는데, 이는 코드에서의 '멀티버스'를 만들고 관리할 수 있게 한다.
코드의 '분기'를 만들어 내어 남이 만들어낸 코드의 특정 부분에서 자신의 코드를 넣을 수 있고, 반대로 자신이 만든 코드를 다른 사람이 수정할 수도 있다. 
또한 코드에 변화를 가져오기 전 상황으로 돌릴 수도 있다. 마치 타임머신처럼 과거의 시간, 다양한 분기점으로 오갈 수 있다. (git의 버전 관리자 특성)
"코드를 잔뜩 고쳤는데 큰 오류가 난다거나 친구와 제 코드를 합쳤더니, 큰 오류가 발생했을 때 변화 내용들을 추적해가며 문제 지점을 발견한 다음, 전부 무를 수 있습니다!" - 강의 중에서

git을 사용하는 데에는 3가지 공간을 알고 있어야 한다.
Working Directory, Staging Area, Local Repository가 그 3개이다.
먼저 'Working Directory'는 코드를 짜고 있는 공간이다. '작업 공간' 이라고도 볼 수 있겠다. 
git의 핵심적인 역할은 코드의 변화를 추적하며 내 임의대로 일정 갯수의 변화들을 모아 저장할 수 있게 하는 것이다. 이를 위해서 'Staging Area'와 'Local Repository'가 구분되어 있다.
Staging Area는 변경된 코드를 저장하는 중간 영역이다. 코드를 수정한 후 git add 명령어를 통해 스테이징 영역에 추가 할 수 있다. 여기에 추가된 파일들은 다음 git commit 명령어를 실행할 때 커밋 대상이 된다.
Local Repository는 Staging Area에 있는 파일들을 커밋하여 저장하는 저장소다. git commit 명령어를 실행하면 staging area에 있는 파일들이 local repository에 저장된다. Local repository에 저장된 커밋들은 변경 내용을 관리하고, 특정 버전을 복원하거나, 변경 내용을 비교하는 등의 작업을 수행할 수 있다.

git은 파일의 변화를 추적한다. 그리고 사용자가 변화를 일으키면 알아서 변화를 찾아낸다. 
git이 찾아낸 변화들 중 '다음 commit'에 포함시킬 변화들을 git add 명령어를 통해 staging area에 넣는다.
따라서 이 변화들을 논리적으로 엮어 이름을 붙여준 뒤 git이 관리하는 local repository에 넘겨줄 떄 git commit 명령어를 통해 넘겨준다.
이렇게 개인의 컴퓨터 내에서 이뤄진 작업들을 서버에 올려 팀원들 간의 원할한 공유를 할 수 있는데, 이를 remote repository라 부르며, github와 같은 서비스를 사용한다. 사용자들은 각자의 local repository의 파일들을 remote repository에 git push를 통해 보내며 git pull을 통해 서버의 파일들을 컴퓨터에 가져올 수 있다. 
