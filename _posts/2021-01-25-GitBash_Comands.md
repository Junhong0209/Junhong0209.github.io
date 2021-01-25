---
layout: post
title: "[GitBash] GitBash 사용법 및 명령어"
subtitle: "GitBash 사용법 및 명령어"
categories: other
tags: Other GitBash GitBash_Commands
comments: ture
---

> GitBash 명령어  
> GitBash 사용법

저번에 GitHub가 무엇 인지 설명하는 글에서 나중에 Git Bash에 대해서 알려준다고 해놓곤 까먹고 있었다...
늦은 것 같지만 지금이라도 올려본다.

> # 커맨드 창 명령어

* 커맨드 창 화면 초기화: Ctrl + L
* 명령어 맨 앞 / 맨 뒤로 이동: Ctrl + A / Ctrl + E
* 디렉토리 이동: cd [이동할 하위 디렉토리 명]
* 디렉토리 삭제: git rm -r [삭제할 디렉토리 명]
* 디렉토리 목록 조회 (2가지): dir / ls
* 파일 내용 조회: cat [파일명]  
  
> #  git config (최초 1회 실행)

***

// 처음 사용시 사용자 등록을 해야한다.

```
// git commit에 사용될 username
$ git config --global user.name "[이름]"

// git commit에 사용될 email
$ git config --global user.email "[이메일 주소]"

// 설정한 내용을 확인할 수 있다.
$ git config --list
```

> # git init

***

// 현재 디렉토리를 로컬 저장소로 설정한다.

```
// 로컬 저장소로 설정
// (master) 브랜치로 보이면 성공!
$ git init
```

> # git status

***

// 로컬 저장소의 현재 상태 보여줌

> # git add

// 파일을 준비 영역으로 (Staging Area)으로 옮김 (GitHub와 연동하려면 git remote로 원격 저장소롸 연결해야 함)

```
// a.html 파일만 추가
$ git add a.html

// 워킹 디렉터리 내 모든 파일을 추가
$ git add .

// 명령 프롬프트에서 상호작용하면서 추가 (나갈땐 q를 입력)
$ git add -i

// 진행중인 파일일 경우, Staging Area에서 워킹 디렉터리로 옮긴다.
$ git rm --cached a.html
$ git rm -r --cached .
```

> # git commit

***

// 준비영역 (Staging Area)의 파일을 로컬 저장소에 저장

```
// 에디터가 출력되고, 에디터에서 커밋 메세지 입력 후 저장하면 커밋된다.
$ git commit

// 간단한 커밋 메세지를 입력 후 커밋
$ git commit -m "커밋 메세지"

// Staging Area에 들어간 파일에 대해서만 (워킹 디렉터리는 적용 X)
$ git commit -a -m "커밋 메세지"
```

> # git remote

****

// 로컬 저장소와 원격 저장소를 연결

```
// GitHub 원격 저장소와 연결한다.
$ git remote add origin [자신의 GitHub 원격 저장소 주소]

// 연결된 원격 저장소를 확인한다.
$ git remote -v
```

> # git push

***

// 원격 저장소에 저장

```
// 원격 저장소에 저장한다.
$ git push -u origin master

// 에러 -! [rejected] master -> master (fetch first)
// 이미 변경된 파일이 원격 저장소에 있을 경우 발생
$ git pull origin master

// 에러 -! [rejected] master -> master (non-fast-forward)
$ git push origin +master
```

> # git branch

****

// 브랜치 생성, 수정 삭제

```
// 브랜치 보기
$ git branch

// 브랜치 생성
$ git branch [브랜치 명]

// 브랜치 수정
$ git branch -m [브랜치 명] [바꿀 이름]

// 브랜치 삭제
$ git branch -d [브랜치 명]
```

> # git checkout

***

// 워킹 디렉토리 소스를 특정 커밋이나 특정 브랜치로 변경

```
// 특정 브랜치로 워킬 디렉터리 변경
$ git checkout [브랜치 명]

// 특정 커밋으로 워킹 디렉터리 변경  
$git checkout [Commit ID]  

// 특정 파일을 해당 브랜치 또는 커밋 상대로 변경 (원복)  
$git checkout [돌아갈 Commit ID] --[파일 경로]  
*충돌 방지를 위해 브랜치 명을 확인하고, 파일 추가 및 수정한 뒤 커밋해야 한다.  

// 브랜치 생성 및 테크아웃을 같이 할 경우  
$git checkout -b develop 
```

> # git merge

***

// 다른 두 개의 브랜치 소스 병합

```
$git checkout master  
$git merge develop  
*같은 파일의 같은 위치의 내용이 변경된 경우 충돌이 발생한다.  
```

