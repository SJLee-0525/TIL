# GIT
#### 분산 버전 관리 시스템: 코드의 변경 이력을 기록하고 협업을 원활하게 하는 도구
- 코드의 버전(history)를 관리
- 개발되어 온 과정 파악
- 이전 버전과의 변경 사항 비교

#### Linus Benedict Torvalds가 개발

**버전 관리:** 변화를 기록하고 추적하는 것
 - 문제가 발생했을 시 기존 버전으로 돌아갈 수 있음
 - 각 버전은 이전 버전으로부터의 변경 사항만을 기록하고 있음 (전체 X)

**중앙 집중:** 버전은 중앙 서버에 저장, 중앙 서버에서 파일을 가져와 다시 업로드

**분산식:** 버전을 여러 개의 복제된 저장소에 저장 및 관리
- 중앙서버에 의존하지 않기 때문에, 서버의 장애나 손실에 대비해 백업과 복구가 용이함
  - 개발자들 간의 작업 충돌을 줄여주고 개발 생산성을 향상
- 인터넷 연결이 없어도 작업을 계속할 수 있음. (로컬에 기록 후 추후 동기화)

## GIT의 3가지 영역
#### Working Directory
- 실제 작업 중인 파일들이 위치하는 영역
#### Staging Area
 - Working Directory에서 변경된 파일 중, 다음 버전에 포함할 파일들을 선택적으로 추가하거나 제외할 수 있는 **중간 준비 영역**
#### Repository
- 버전(Commit) 이력과 파일들이 영구적으로 저장되는 영역
- 모든 버전과 변경 이력이 기록됨

> **Commit: 버전**
> - 변경된 파일들을 저장하는 행위
> - 모든 버전과 변경 이력이 기록됨

## 명령어
#### git init: 로컬 저장소 설정 (초기화)
- git의 버전 관리를 시작할 디렉토리에서 진행
- git을 선언하면 master 딱지가 생성
- 하위 디렉토리 전부에 영향
   - 만약 하위 디렉토리에 또 init 선언을 하면, 상위 디렉토리에서 찾을 수 없으니 주의.. 
   - 가장 바깥쪽의 git 저장소가 안쪽의 git 저장소의 변경사항을 추적하지 못함
   - 위와 같은 실수를 저질렀을 때 숨김 파일 중에서 .git을 삭제하면 해결

#### git add 파일명: 변경 사항이 있는 파일을 Staging Area에 추가 (2순위)
- **git add . :** 현재 위치의 변경 사항을 전부 추가
- 변경된 파일을 업로드 하는 것이 아님.
- 생성, 수정 등의 변화를 업로드 <-> 드라이브와는 다름

#### git commit: Staging Area에 있는 파일들을 저장소에 기록 (3순위)
- 해당 시점의 버전을 생성하고 변경 이력을 남기는 것
- **git commit -m "fisrt commit"** (-m: massage: 버전이름)
- 노란색 난수로 구분하기 때문에, **commit 명은 중복되어도 상관 없음**
  
#### git status: Git의 상태를 확인 (1순위)
- **git log:** status가 보여주지 history 보기
- **git log —oneline:** commit 목록 한 줄로 보기
- **빨강:** 중간 영역으로 가지 않음
- **초록:** 중간 영역으로 감
- Untracked → New file → Modified → Modified → Nothing to commit …

#### git config: Git의 설정
- **git config —global [user.email](http://user.email) “이메일”**
- **git config —global [user.name](http://user.name) “이름”**
    - GIT LAB에 맞춰주는 게 좋음
    - **처음 한 번만 설정하면 됨**
- **git config —global -l:** git global 설정 정보 보기

#### git remote add origin remote_repo_url: 로컬 저장소에 원격 저장소 추가
- 별칭을 추가하는 과정: origin = 1번째 저장소의 암묵적인 별칭
- **git remote -v :** 경로 등록된 것 확인
- 업로드: push / 다운로드: pull or clone
- **git push origin master:** 원격 저장소에 commit 목록을 업로드
- **git pull:** push와 대조 / 원격 저장소가 업데이트 되었기 때문에 변경 사항만을 다운로드
    - 버전 관리가 잘 돼야 pull이 잘 됨.
- **git clone remote_repo_url:** 저장소 전체를 복제 / 처음 받을 때 사용함
    - clone으로 받은 프로젝트는 이미 git init 되어있기 때문

#### git revert <commit id>: 재설정
- 변경 사항을 안전하게 실행 취소할 수 있도록 도와주는 순방향 실행 취소 작업 (특정 commit을 없었던 일로)
- commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit을 생성 (없었던 일로 만든 다응메 새로운 미래를 만듦)  
  -> git에서 기록이 손실되는 것을 방지하며 기록의 무결성과 협업의 신뢰성을 높임  
  - commit을 없애는 것은 아님. 없었던 일로 처리하는 것: **commit의 수 유지**
  - **git에 파일이 삭제가 된 채로 업로드가 되지 않고, commit의 개수가 달라지면 협업에 지장** -> 그렇기 떄문에 파일이 지워지더라도 commit을 남겨둠
- 노란색 난수값이 commit의 id (다 작정할 필요는 없고, 앞의 4~5개 정도만)
- 여러 개를 한 번에 revert 하고 싶으면, **id를 공백으로 구분해 나열해도 됨**
- 연속되는 commit을 한 번에 revert 하고 싶으면 **처음과 끝 commit을 ..으로 구분**
- 실행하면 **VIM**이 실행됨. 알아서 commit 메시지를 생성해 주긴 함.
   - **명령 모드:** 커서 이동 불가능 / **esc**
   - **입력 모드:** 커서 이동 가능 / **i (insert)**
      - **이름 수정:** 입력 모드 -> 이름 입력 -> 명령 모드 -> **shift + ;** -> **wq (write, quit)**
- **git revert --no-edit <id>:** commit 메시지 작성을 위한 편집기를 열지 않음
- **git revert --no-commit <id>:** 자동으로 commit 하지 않고 **Staging Area**에만 업로드

#### git restore 파일명: Modified 상태의 파일 되돌리기 (수정 전으로)
- **Working Directory**에서 파일을 수정한 뒤 수정 사항을 취소한 후 원 모습대로 되돌리는 작업
- 원래 파일로 덮어쓰는 원리: **수정된 내용은 전부 사라지고 복원 불가능**

#### Unstage: **Staging Area**에서 **Working Directory**로 반환하는 작업
- **git rm --cached 파일명:** git 저장소에 **commit이 없을 경우**
- **git restore --staged 파일명:** gut 저장소에 **commit이 존재하는 경우**

**git status를 하면 git이 알려줌**

#### git commit --amend: 바로 직전에 생성한 commit 수정하기
- Staging Area가 **비어있을 때: 바로 직전의 commit 메시지 수정**  
- Staging Area에 **파일이 있을 때: 바로 직전의 commit에 누락된 파일 업로드**  
   - 실행하면 **VIM**이 실행됨. 알아서 commit 메시지를 수정해주긴 함.  

      - **명령 모드:** 커서 이동 불가능 / **esc**
      - **입력 모드:** 커서 이동 가능 / **i (insert)**  
        **이름 수정**: 입력모드 -> 이름 입력 -> 명령모드 -> **Shift + ; + wq** (write, quit)  

-> **메시지만 수정하는 게 아닌, commit 자체가 바뀜: 협업시 싱크가 깨질 수 있기에 주의**


## 원격 저장소
#### 코드의 버전 관리 이력을 온라인 상의 특정 위치에 저장해, 여러 개발자가 협업하고 코드를 공유할 수 있는 저장 공간

- GitLab, **GitHub**, Bitbucket
- 파일을 올리는 드라이브의 개념이 아님.
- **변동 내역이 있는 Commit을 올리는 것이기 때문에, add commit이 필수적으로 선행되어야 함.**
- 또 변동 내역을 업로드 할 때도 전부 업로드 하는 것이 아닌, 변동된 것만 업로드 함.
- 다른 로컬 저장소가 원격 저장소를 공유할 수 있고, 명칭 또한 달리 부를 수 있음
- 깃헙에서 **Add a README file를 체크 후 사용할 경우** 이미 원격 저장소에 commit이 하나 추가된 채로 시작함: **반드시 clone으로 받고 시작해야함!!** 앞의 방법으로 하면 충돌납니다?

## gitignore
#### 주의: 이미 git의 관리를 받은 이력이 있는 파일이나 디렉토리는 나중에 gitignore에 작성해도 적용되지 않음.
-> 되도록 초반에 .gitignore 설정을 완료하자!
> hㅏㅏㅏ 근데 제가 그 설정을 안 했어요...  
> 다 지우고 새로 만들 필요는 없을 거예요... 난 믿어  
> **ㅔ제발**

> **해결**  
> 파일이 이미 들어간 것이 아니라면 상관이 없었음
> 만약 파일이 들어가 있었다면 `git rm -r --cached .`를 활용해서 캐시를 제거하고 사용하면 된다고 하셨음!

- **Git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는데 사용되는 텍스트 파일**
- **파일명: .gitignore / 내부에 무시할 파일명 첨부**

> [**활용 사이트**](https://www.toptal.com/developers/gitignore/)
> 