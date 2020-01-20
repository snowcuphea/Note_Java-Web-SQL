# Git

> Git은 분산형버전관리시스템(DVCS)이다.
>
> 소스코드 형상 관리 도구로써, 작성되는코드의 이력을 관리한다.

# 0. 기본 설정

아래의 설정은 이력 작성자(author)를 설정하는 것으로, 컴퓨터에서 최초에 한번만 설정하면 된다.

```bash
$ git config --global user.name snowcuphea <<본인 github 계정
$ git config --global user.email snowcuphea@gmail.com << 본인 github 가입 이메일로 변경
```



## 1. 로컬 저장소(repository) 활용

### 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Useop/TIL/.git/
(master) $
```

* (master)는 현재 있는 브랜치 위치를 뜻하며, `.git `폴더가 생성된다.
* 해당 폴더를 삭제하게 되면 모든 `git` 과 관련된 이력이 삭제된다.



## 2. add

이력을 확정하기위해서는 add 명령어를 통하여 `staging area` 에 `stage` 시킨다.

```bash
$ git add .				# 현재 디렉토리를 stage
$ git add README.md		# 특정 파일을 stage
$ git add images/		# 특정 폴더를 stage
```

stage 무대

커밋을 하는 거를 스냇샵을 찍는다 라고 한다. 

add를 한 이후에는 항상 `status`명령어를 통해 원하는 대로 되었는지 확인한다.

```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git.md
        new file:   images/catt.jpg
        new file:   images/image-20191205161852154.png
        new file:   markdown.md

```



# 3. commit

`git` 은 `commit` 을 통해 이력을 남긴다. 

커밋 시에는 항상 메시지를 통해 해당 이력의 정보를 나타내야 한다.

```bash
$ git commit -m 'Init'
[master (root-commit) bda6d07] Init
 4 files changed, 144 insertions(+)
 create mode 100644 git.md
 create mode 100644 images/catt.jpg
 create mode 100644 images/image-20191205161852154.png
 create mode 100644 markdown.md


```

커밋 목록은 아래의 명령어를 통해 확인 가능하다.

```bash
$ git log
commit bda6d0785f0db062181ddbb14eb9db834216e922 (HEAD -> master)
Author: snowcuphea <snowcuphea@gmail.com>
Date:   Thu Dec 5 16:52:23 2019 +0900

    Init

```

## 2. 원격 저장소(remote repository) 활용

> 원격 저장소는 다양한 서비스를 통해 제공받을 수 있다.
>
> github, gitlab, bitbucket

### 1. 원격 저장소 등록

```bash
$ git remote add origin https~~~~(URL)
```



원격 저장소(remote)를 `origin` 이라는 이름으로 해당 url로 설정한다. // 원격저장소는 하나가 아닌 여러개 할 수 있다. 보통 origin 으로 많이 설정한다.

등록된 원격 저장소는 아래의 명령어로 확인할 수 있다.

등록은 한번만 실행하면 된다.

```bash
$ git remote -v
```



### 2. 원격 저장소 push

```bash
$ git push origin master
```

origin 원격 저장소에 push 하게 되며, github에서 확인할 수 있다.

이후 작업 과정에서는 add -> commit으로 이력을 남기고 push로 업로드 하면 된다.



집 폴더를 만들고, 거기다가 git bash

그담에 레포지토리 들어가서 clone or downloads누르면 https 주소 복사해서

복사한담에 명령창에

git clone 주소붙여넣기 

하면 집 폴더 안에 해당 폴더가 생긴다. 