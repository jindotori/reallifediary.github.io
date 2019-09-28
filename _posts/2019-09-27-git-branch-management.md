---
title: Git branch 관리
layout: post
summary: Git branch 효과적으로 관리하기
featured-img: github
---
## 개요
회사에서 진행하는 프로젝트가 있다. 혼자 관리하는 소스라 굳이 버전 관리할 필요가 있겠나 싶어서 develop 브랜치에서만 개발하였다. 이렇게 하다보니 혼자 관리하는 소스라도 갑작스런 roll back이나 다른 버전으로 개발해야 할 경우가 생겼다. 이번 기회에 혼자서라도 브랜치 관리하면 효과적이고 효율적으로 개발할 수 있을 것 같아 정리한다.

## 전반적인 branch 관리
출처: [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)


![totalBranch](https://gmlwjd9405.github.io/images/types-of-git-branch/total-branch.png)


### 메인 브랜치
- master
- develop

![mainBranch](https://nvie.com/img/main-branches@2x.png)

### 보조 브랜치
- Feature
- Release
- Hotfix

##### Feature 브랜치
branch off from develop
merge back into develop
naming: anything except master, develop, release-* or hotfix-*

![feature](https://nvie.com/img/fb@2x.png)

##### Release 브랜치
branch off from develop
merge back into master and develop
naming: release-*

##### Hotfix 브랜치
branch off from master
merge back into develop and master
naming: hotfix-*

![hotfix](https://nvie.com/img/hotfix-branches@2x.png)
