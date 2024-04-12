# Move Full Git Repository

> 모듈 개발을 진행할 때 마다 그 때의 버전으로 저장소를 새로 생성하던 탓에 
> 깃 푸시 이력을 찾을 수 없어 유지보수에 어려움을 겪어왔다.
> 
> 회사 특성 상 내부망과 외부망을 번갈아가며 사용하다보니
> 그 불편함이 극대화되었다.
> 
> 그래서 Repository의 이력을 통째로 옮겨보기로 했다.

*****

### 1. 새 폴더 생성

    새 로컬 저장소로 사용할 폴더를 생성한다.

### 2. 새 폴더에 기존 저장소 Clone
     
    ` git clone --mirror {oldRepositoryUrl} .\ `

### 3. 기존 원격서버와 연결 해제

    ` git remote rm origin `

### 4. 새 저장소 주소로 연결

    ` git remote add origin {newRepositoryUrl} `

### 5. 새 저장소로 전부 업로드

    ` git push --mirror `


