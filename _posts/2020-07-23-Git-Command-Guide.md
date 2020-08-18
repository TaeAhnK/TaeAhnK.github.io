---
layout: post
title:  "급할 때 보기 위한 Git Commands"
date:   2020-07-23 19:30:00 +0900
categories:
  - ETCs
tags: 
  - github
  - git
---

## 시작하기

| Command                                  | 설명 |
|---|---|
| git init                                 | 디렉토리를 git에 사용하도록 Repository 생성              |
| git config user.name "**사용자 이름**"      | 작성자 이름 설정                                     |
| git config email.name "**이메일**"         | 작성자 이메일 설정                                   |
| git remote add origin **Github 주소**     | Github 주소를 Remote Repository로 설정              |
| git help **명령어**                        | 관련 명령어 설명 출력                                |
| git status                               | git의 상태 출력                                    |
| git config alias.**새로운이름** **커맨드**    | 커맨드 단축어 생성                                   |
| git push --set-upstream origin master    | Local Repository를 처음으로 Remote Repository로 보냄 |
| git config --global core.quotepath false | 한글 출력 오류 해결                                  |

***

## Commit

| Command | 설명 |
|---|---|
| git add **파일명** | Commit할 파일을 Staging Area에 추가 |
| git add **디렉토리** | Commit할 디렉토리를 Staging Area에 추가 |
| git add . | 변경된 모든 파일을  Staging Area에 추가 |
| git commit -m "**Commit Message**" | Repository에 저장 |
| git commit | Commit Message를 남길 수 있는 텍스트 에디터가 열림 |
| git commit --amend | 최신 Commit을 수정하며 Commit |
| git reset | Staging Area에서 변경된 파일 제거 |

***

## Remote Repository

|Command|설명|
|------|------|
|git push -u origin master|Remote Repository에 push|
|git push|변경 사항을 Remote Repository에 저장|
|git pull|Remote Repository의 변경사항을 Local Repository에 적용|
|git clone **주소**|Repository 다운 받기|
|git fetch|Remote Repository에 dlTsms Branch를 가져오고, Merge는 하지 않음|

***
## Log

|Command|설명|
|------|------|
|git log|Commit 히스토리 보기
|git log --pretty=oneline|한줄씩만|
|git show **Commit ID**|Commit과 이전 Commit의 차이 출력 ( --- 이전 , +++ 이후)|
|git diff **Commit ID1** **Commit ID2**|Commit의 변화 출력|
|git blame **파일명**|파일의 코드와 Commit 정보를 대치해 출력|

***
## Reset

|Command|설명|
|------|------|
|git reset --hard **Commit ID**|모든 파일을 Commit ID의 상태로 돌아가기 (HEAD가 해당 아이디를 가르킴)|
|git reset --soft **Commit ID**| Repository를 Commit ID의 상태로|
|git reset --mixed **Commit ID**|Staging Area까지 Commit ID의 상태로|
|git reset HEAD^|HEAD 이전 Commit으로 초기화|
|git reset HEAD~4|HEAD 4단계 전의 Commit으로 초기화|

***
## Tag

|Command|설명|
|------|------|
|git tag 태그이름 **Commit ID**|Commit에 Tag달기|
|git show 태그이름|Tag 달린 Commit만 보여주기|

***
## Branch

|Command|설명|
|------|------|
|git branch **Branch Name**|Branch 추가|
|git checkout **Branch Name**|Branch 변경|
|git branch|모든 Branch 보기|
|git branch -d **Branch Name**|Branch 삭제|
|git checkout -b **Branch Name**|Branch 생성 후 이동|
|git merge **Branch Name**|현재 Branch에 Branch 이름을 합함|
|git merge --abort |Merge 취소|

***
## Commit Message Rule

1. 제목과 상세 설명 사이 한 줄을 비운다.
2. 제목 뒤에 .을 찍지 않는다.
3. 제목의 첫 글자는 대문자로 한다.
4. 제목은 명령조로 쓴다.
5. 상세 내용에는 왜 수정했는 지, 어떤 문제를 해결했는 지, 어떤 효과를 내는 지 쓴다.

- 하나의 Commit에는 하나의 수정사항, 하나의 이슈를 해결한 내용만 넣는다.
- 에러가 발생하지 않는 상태일 때만 Commit한다.
