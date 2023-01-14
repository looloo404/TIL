
# Branch
---

## (1)Branch란?


<img src = "https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d6378065-5864-4832-8122-0fde3eb4f6ec/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230112%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230112T082915Z&X-Amz-Expires=86400&X-Amz-Signature=a215d0b36ba4d477c4aec4de2b6b59ddc2a81fb7d0b4edda1a126ce2f9938087&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject" width = "75%" height = "100%">  

- Branch는  <span style="color:red">나뭇가지</span>라는 뜻의 영단어입니다.
- 즉 <span style="color:red">브랜치</span>란 나뭇가지처럼 여러 갈래로 작업 공간을 나누어 ***독립적으로 작업***할 수 있도록 도와주는 Git의 도구입니다.

### **장점**
1. 브랜치는 독립 공간을 형성하기 때문에 원본(master)에 대해 안전
2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적인 개발이 가능합니다.
3. 특히나 Git은 브랜치를 만드는 속도가 굉장히 빠르고, 용량도 적게 듭니다.

## (2)git branch
> branch <span style="color:red">조회, 생성, 삭제 등</span>브랜치와 관련된 Git 명령어

```bash
#브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$git branch -r

#새로운 브랜치 생성
$git branch <브랜치 이름>

#특정 커밋 기준으로 브랜치 생성
$git branch <브랜치 이름> <커밋 ID>

#특정 브랜치 삭제
$git branch -d <브랜치 이름> #병합된 브랜치만 삭제 가능
$git branch _D <브랜치 이름> #(주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```
## (3)git switch
 
> 현재 브랜치에서 다른 브랜치로 <span style="color:red">HEAD</span>를 이동시키는 명령어
> 
><span style="color:red">HEAD</span>란 현재 브랜치를 가리키는 포인터를 의미합니다.

<br/>

# Brach scenario

## (1)사전 세팅
1. 새로운 디렉토리를 하나 만듭니다.
``` bash
$ mkdir git branch-practice
$ cd git-branch-practice
$ pwd
```
2. Git 저장소를 생성합니다.
``` bash
$ git init
Initialized empty Git repository in C:/Users/kyle/git-branch-practice/.git/
```
3. test.txt를 생성하고 각각<span style = "color:red"> master-1, master-2, master-3</span> 이라는 내용을 순서대로 입력하여 커밋 3개를 입력합니다.
``` bash
$ touch test.txt

test.txt에 master-1 작성
$ git add .
$ git commit -m "master-1"

test.txt에 master-2 작성
$ git add .
$ git commit -m "master-2"

test.txt에 master-3 작성
$ git add .
$ git commit -m "master-3"
```

4. <span style = "color:red">git log --oneline</span>을 입력하였을 때 아래와 같이 나와야 정상입니다.
총 3개의 버전이 master 브랜치에 만들어졌습니다.

```bash
$ git log --oneline
0604dcd (HEAD -> master) master-3
9c22c89 master-2
3d71510 master-1
```

<img src = "https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcc3011f7-0e5d-451c-9139-495943965203%2FUntitled.png?id=19bf8527-833d-4537-9ec2-5b8ac04b3994&table=block&spaceId=f7ab64f0-6613-4035-b609-06b6865d9b61&width=1600&userId=a3b8ca82-fbbc-4a16-89ea-34670cda81f6&cache=v2" width = "75%" height = "100%">



## (2) 브랜치 생성 및 조회

1. 현재 위치(master 브랜치의 최신 커밋)에서 <span style = "color:red">login</span>이라는 이름으로 브랜치를 생성합니다.
``` bash

$git branch login
```


2.2. login브랜치가 잘 생성되었는지 확인합니다.
    
`* master`의 의미는 현재 HEAD가 가리키는 브랜치는 `master`라는 것입니다

``` bash
$ git branch
  login
* master
```
3. `git log --oneline`을 입력했을 때 아래와 같이 나와야 정상입니다.
    
    `0604dcd` 커밋 기준으로 `master`와 `login`브랜치가 위치한 것을 볼 수 있습니다.$ git log 

``` bash
$ git log --oneline
0604dcd (HEAD -> master, login) master-3
9c22c89 master-2
3d71510 master-1
```

4. `master` 브랜치에서 1개의 커밋을 더 작성합니다.
```bash
test.txt에 master-4 작성
$ git add .
$ git commit -m "master-4"

```

<img src = "https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb98030f5-945f-40a5-83f1-b4a4800711ec%2FUntitled.png?id=f94b2d34-8286-451f-b1c3-afdd32585e88&table=block&spaceId=f7ab64f0-6613-4035-b609-06b6865d9b61&width=1600&userId=a3b8ca82-fbbc-4a16-89ea-34670cda81f6&cache=v2" width = "70%" height = "50%">

## 브랜치 이동
1. 현재 브랜치와 커밋의 상태는 다음과 같습니다.
```bash
$ git log --oneline
5ca7701 (HEAD -> master) master-4
0604dcd (login) master-3
9c22c89 master-2
3d71510 master-1
```

2. 이 때 `login` 브랜치로 이동한다면?
```bash
git switch login
```
<code> master 브랜치의 test.txt에 작성한 master-4가 지워졌습니다!</code>

```bash
# login 브랜치의 test.txt
master-1
master-2
master-3
```

 3. 그리고 `git log --oneline`을 입력하면 아래와 같이 나타납니다.
    
    이제 `HEAD`는 `login` 브랜치를 가리키고, `master` 브랜치가 보이지 않습니다.

```bash
$ git log --oneline
0604dcd (HEAD -> login) master-3
9c22c89 master-2
3d71510 master-1
```
4. master 브랜치는 삭제된 걸까요?
    
    아닙니다! 브랜치를 조회 해보면 다음과 같이 나타납니다.

    HEAD가 `login` 브랜치를 가리키면서, log도 `login` 브랜치 기준으로 보이는 것이었습니다.

```bash
$ git branch
* login
  master
```

5. git log --oneline --all을 입력하면 모든 브랜치의 로그를 볼 수 있습니다.

```bash
$ git log --oneline --all
5ca7701 (master) master-4
0604dcd (HEAD -> login) master-3
9c22c89 master-2
3d71510 master-1
```
6. 현재까지의 결과

<img src = "https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fdd3c4b03-5d20-4f80-a13f-df5c187552aa%2FUntitled.png?id=7f446484-fd44-486d-a3b8-92df7a7dcf9d&table=block&spaceId=f7ab64f0-6613-4035-b609-06b6865d9b61&width=2000&userId=a3b8ca82-fbbc-4a16-89ea-34670cda81f6&cache=v2" width = "70%" height = "50%">


<br/>


💡 즉 브랜치를 이동한다는건 HEAD가 해당 브랜치를 가리킨다는 것을 의미하고
브랜치는 최신 커밋을 가리키므로, **HEAD가 해당 브랜치의 최신 커밋을 가리키게 됩니다.

따라서 워킹 디렉토리의 내용도 HEAD가 가리키는 브랜치의 최신 커밋 상태로 변화합니다.


## (4) login 브랜치에서 커밋 생성

1. test.txt 파일에 login-1이라고 작성합니다.


```bash
# login 브랜치의 test.txt
master-1
master-2
master-3
login-1
```


2. 추가적으로 test_login.txt도 생성하고 login-1이라고 작성해봅시다.
```bash
$ touch test_login.txt

# 이후 test_login.txt에 작성
login-1
```
3. 커밋을 생성합니다.
```bash
$ git add .
$ git commit -m "login-1"
```
4. `git log --oneline --all --graph`를 통해 아래와 같은 내용을 확인합니다.
    
    `master` 브랜치와 `login` 브랜치가 다른 갈래로 갈라진 것을 확인할 수 있습니다.
    
    ```bash
    $ git log --oneline --graph --all
    * 3b0a091 (HEAD -> login) login-1
    | * 5ca7701 (master) master-4
    |/
    * 0604dcd master-3
    * 9c22c89 master-2
    * 3d71510 master-1
    ```


5. 현재까지 결과
    
    ![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F5932ce06-f1c4-41a3-86fe-efc431249abd%2FUntitled.png?id=b50e05ce-e129-496c-acc8-90a77519ba22&table=block&spaceId=f7ab64f0-6613-4035-b609-06b6865d9b61&width=1600&userId=a3b8ca82-fbbc-4a16-89ea-34670cda81f6&cache=v2)


