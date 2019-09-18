---
title: Github 잔디가 안심어져요
layout: post
summary: Github 잔디(Contribution) 안심어질 때 확인 사항
featured-img: github
---

![github](data:image/png;base64,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)

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