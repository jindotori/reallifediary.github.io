---
title: Github 잔디가 안심어져요
layout: post
summary: Github 잔디(Contribution) 안심어질 때 확인 사항
---

Github 무료로 풀려서 Bitbucket 에서 Github으로 옮긴 후 활동량 증가를 위해 commit을 열심히 올렸으나 잔디가 채워지지 않았다.
열심히 찾아본 결과 Github에 등록된 계정 정보와 git에서 commit 하는 계정 정보가 동일해야 한다는 것을 알았다.


1. 작업중인 폴더로 가서 아래 명령어를 사용해서 user 및 email이 등록되어 있는지 확인
~~~
git config --list
~~~
2. 아래 명령어로 계정 정보 입력한다. (다른 프로젝트에 영향가지 않도록 local로 설정함. 모든 설정 바꾸고 싶으면 local 대신 global 명령어 사용)
~~~
git config --local user.name "[Your name]" 로 이름 수정
git config --local user.email "[Your Email]" 로 이메일 수정
~~~

그리고 나서 commit 후 push하면 바로 잔디가 심어진다!
