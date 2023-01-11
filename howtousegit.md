
# Git 초기 설정

최초 한 번만 설정, 매번 Git을 사용할 때마다 설정할 필요 x

  ```bash
   $ git config --global user.name "이름"
   $ git config --global user.email "이메일"
```
<br/>

# 로컬 저장소
![Stage Area](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7142d992-3d01-481c-9d4e-e818c6e185d8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230111%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230111T081250Z&X-Amz-Expires=86400&X-Amz-Signature=8f1963d4a54da5b0bcd86fa784dc422afdc36c1fb7f15228064e1c03a3780ede&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- Working Directory (= Working Tree): 사용자의 일반적인 작업이 일어나는 곳
- Staging Area(= Index) : 커밋을 위한 파일 및 폴더가 추가되는 곳
- Repository : staging area에 있던 파일 및 폴더의 변경사항(커밋)을 저장하는 곳
- Git은 working Directory -> Staging Area -> Repository의 과정으로 버전 관리를 수행합니다.


### git init 
``` $ git init```

- 현재 작업중인 디렉토리를 Git으로 관리한다는 명령어
- .git이라는 숨김폴더가 생성되고, 터미널에는 (master)라고 표기된다.


<h3><span style="color:red">! 주의 사항 </span></h3>

``` code block multiline
1. 이미 Git 저장소인 폴더 내에 또 다른 Git 저장소를 만들지 않는다.

2. pwd로 자신의 위치를 확인하자. 실수로 C드라이브에 했다가는 컴퓨터가 버티지 못한다.
```

### git status

<br/>

``` bash
$ git status
```
- Working Directory와 Staging Area에 있는 파일의 현재 상태를 알려주는 명령어
- 어떤 작업을 시행하기 전에 수시로 status를 확인하면 좋다.
- 상태
    1. <span style="color:red">untracked </span>: Git이 관리하지 않는 파일(한 번도 staging Area에 올라간 적 없는 파일)
  
    2. <span style="color:red">tracked </span> : Git이 관리하는 파일
        - Unmodified : 최신 상태
        - Modified : 수정되었지만 아직 Staging Area에는 반영하지 않는 상태
        - Staged : Staging Area에 올라간 상태

<br/>
        
  ![File's Lifecycle](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/67719520-a1d8-4cbb-81dd-49dea429a7f4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230111%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230111T083653Z&X-Amz-Expires=86400&X-Amz-Signature=07bf011dada92b57119986ee7bfc0d21907e0f41fc272aac470dd4691454fb2d&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


<br/>

### git add

``` bash
# 특정 파일
$ git add a.txt

#특정 폴더
$ git add my_folder/

#현재 디렉토리에 속한 파일/폴더 전부
$ git add .
```

- Working Directory에 있는 파일을 Staging Area로 올리는 명령어
- GIt이 해당 파일을 추적(관리)할 수 있도록 만듭니다.
- <span style="color:red">untracked, Modified -> staged</span>로 상태를 변경합니다. 

```bash
$ git status

On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        howtousegit.md

nothing added to commit but untracked files present (use "git add" to track)
```

``` bash
$ git add howtousegit.md
```

### git commit

``` bash
$ git commit -m "first commit"
```
  - Staging Area에 올라온 파일의 변경 사항을 하나의 버전(커밋)으로 저장하는 명령어
  - <span style="color:red">커밋 메시지</span>는 현재 변경 사항들을 잘 나타낼 수 있도록 의미있게 작성하는 것을 권장
  - <span style="color:red">(root commit)</span>은 해당 커밋이 최초의 커밋일 때 표시됩니다. 이후 커밋부터는 사라집니다.

### git log
``` bash
$ git log

commit 9200a427999525289d6c56a0aa3abdcf761541d7 (HEAD -> master, origin/master)
Author: looloo404 <looloo404@hanmail.net>
Date:   Wed Jan 11 16:36:10 2023 +0900

    TIL230111
```

- 커밋의 내역(<span style="color:red">ID, 작성자, 시간, 메세지 등</span>)을 조회할 수 있는 명령어
- 옵션
    - <span style="color:red">--online</span> : 한 줄로 축약해서 보여줍니다.
    - <span style="color:red">--graph</span> : 브랜치와 머지 내역을 그래프로 보여줍니다.
    - <span style="color:red">--all</span> : 현재 브랜치를 포함한 모든 브랜치의 내역을 보여줍니다.
    - <span style="color:red">-p</span> : 파일의 변경 내용도 같이 보여줍니다.
    - <span style="color:red">-2</span> : 원하는 갯수 만큼의 내역을 보여줍니다.(2말고도 임의의 숫자 가능)

</br>

### 한눈에 보는 Git 명령어

![이미지](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c86c667a-616f-45b6-892e-15da6a3c494e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230111%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230111T085958Z&X-Amz-Expires=86400&X-Amz-Signature=0a69ce81efc3d816e0b7cba46dc9bae26169ede57239f8b0658cb3390ce99c57&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)