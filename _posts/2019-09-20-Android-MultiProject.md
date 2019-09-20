---
title: Android Multi Project
layout: post
summary: 하나의 프로젝트에 Android App 과 aar 프로젝트 링크 연동시키기
---

Android App Project 에서 aar 파일 로컬로 추가 시키지 않고 링크 연결해서 빌드하는 방법이다.
aar 프로젝트 코드 수정 할 때마다 App 프로젝트로 추가시키는 번거로움 없이 하나의 프로젝트에서 수정 및 빌드할 수 있어서 반복 작업하는 번거로움이 없어진다.

### 루트 프로젝트 gradle 경로
```
/settings.gradle
/AARproject/build.gradle
/AppProject/build.gradle
```

### /settings.gradle
```
include ':AARProject'
project(':AARProject').projectDir=new File('AARProjectPath')
```

### /AppProject/build.gradle
```
dependencies {
  implementation project(':AARProject')
}
```

이렇게 하면 끝.
