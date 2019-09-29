---
title: Git branch 관리
layout: post
summary: Git branch 효과적으로 관리하기
featured-img: github
categories: Software 
---
# 개요

회사에서 진행하는 프로젝트가 있다. 혼자 관리하는 소스라 굳이 버전 관리할 필요가 있겠나 싶어서 develop 브랜치에서만 개발하였다. 이렇게 하다보니 혼자 관리하는 소스라도 갑작스런 roll back이나 다른 버전으로 개발해야 할 경우가 생겼다. 이번 기회에 혼자서라도 브랜치 관리하면 효과적이고 효율적으로 개발할 수 있을 것 같아 정리한다.

# 전반적인 branch 관리

출처: [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)

![totalBranch](https://gmlwjd9405.github.io/images/types-of-git-branch/total-branch.png)


## 메인 브랜치
- master
- develop

![mainBranch](https://nvie.com/img/main-branches@2x.png)

## 보조 브랜치
- Feature
- Release
- Hotfix

## Feature 브랜치
- branch off from develop
- merge back into develop
- naming: anything except master, develop, release-* or hotfix-*

*Creating Feature Branch*
~~~
$ git checkout -b myfeature develop
Switched to a new branch "myfeature"
~~~

*feature 브랜치 작업 완료 후*
~~~
$ git checkout develop
Switched to branch 'develop'
$ git merge --no-ff myfeature
Updating ea1b82a..05e9557
(Summary of changes)
$ git branch -d myfeature
Deleted branch myfeature (was 05e9557).
$ git push origin develop
~~~


![feature](https://nvie.com/img/fb@2x.png)

#### Release 브랜치
- branch off from develop
- merge back into master and develop
- naming: release-*

*Creating Release Branch*
~~~
$ git checkout -b release-1.2 develop
Switched to a new branch "release-1.2"
$ ./bump-version.sh 1.2
Files modified successfully, version bumped to 1.2.
$ git commit -a -m "Bumped version number to 1.2"
[release-1.2 74d9424] Bumped version number to 1.2
1 files changed, 1 insertions(+), 1 deletions(-)
~~~

*Release 브랜치 작업 완료 후*
~~~
$ git checkout master
Switched to branch 'master'
$ git merge --no-ff release-1.2
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2
~~~

#### Hotfix 브랜치
- branch off from master
- merge back into develop and master
- naming: hotfix-*

*Hotfix 브랜치 만들기*
~~~
$ git checkout -b hotfix-1.2.1 master
Switched to a new branch "hotfix-1.2.1"
$ ./bump-version.sh 1.2.1
Files modified successfully, version bumped to 1.2.1.
$ git commit -a -m "Bumped version number to 1.2.1"
[hotfix-1.2.1 41e61bb] Bumped version number to 1.2.1
1 files changed, 1 insertions(+), 1 deletions(-)
~~~

*Hotfix 브랜치 작업 완료*
- Hotfix 브랜치는 작업 완료 후 master, develop 브랜치 모두 merge해야 함.

(master branch merge)
~~~
$ git checkout master
Switched to branch 'master'
$ git merge --no-ff hotfix-1.2.1
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2.1
~~~

(develop branch merge)
~~~
git checkout develop
Switched to branch 'develop'
$ git merge --no-ff hotfix-1.2.1
Merge made by recursive.
(Summary of changes)
~~~

- merge 완료 후 브랜치 삭제
~~~
$ git branch -d hotfix-1.2.1
Deleted branch hotfix-1.2.1 (was abbe5d6).
~~~

![hotfix](https://nvie.com/img/hotfix-branches@2x.png)
