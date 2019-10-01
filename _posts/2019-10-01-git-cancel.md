---
title: Git add 취소하기
layout: post
summary: Git add 취소하기
featured-img: github
categories: Git
---

## git add 취소하는 방법
#### (파일 상태를 Unstage로 변경하기)

아래와 같이 git add * 명령을 사용하여 Staging Area에 넣은 경우,
Staging Area에 넣은 파일을 unstage 상태로 돌리고 싶을 때가 있다.

~~~
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   settings.gradle
        modified:   spooncast/src/main/java/co/spoonme/live/AddLiveActivity.kt

~~~


이때, git reset HEAD [file] 명령어를 통해 git add를 취소할 수 있다.
(뒤에 파일명이 없으면 add한 파일 전체를 취소한다.)
~~~
$ git reset HEAD settings.gradle
~~~

git staus 로 확인한 결과, setting.gralde 만 unstaged 상태로 돌아온 것을 확인할 수 있다.
~~~
Unstaged changes after reset:
M       settings.gradle
U       spooncast/build.gradle
~~~
