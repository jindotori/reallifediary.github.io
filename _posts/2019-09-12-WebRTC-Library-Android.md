---
title: WebRTC Android library 빌드
layout: post
summary: Android OS에서 WebRTC 커스터마이징 시 필요한 빌드 방법.
featured-img: webrtc
categories: WebRTC
---
# libjingle_peerconnection_so 추출하기(Android)

WebRTC 를 안드로이드로 빌드 하는 방법에 대해서 알아 본다. 아래 과정을 순서대로 따라하면 된다.
나의 경우, 맥북에 Virtual Box상 우분투를 설치하여 우분투에서 소스 다운 및 빌드를 진행하였다.

---
### WebRTC android 참고 문서 및 소스
https://webrtc.org/
webrtc 안드로이드 문서
https://webrtc.org/native-code/android/
소스 주소
https://chromium.googlesource.com/external/webrtc.git

---
### 터미널에서 폴더생성
mkdir webrtc
cd webrtc

---
## Prerequisite software


### Depot Tools clone
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git


### Depot Tools 임시 Path 등록
export PATH=`pwd`/depot_tools:"$PATH"

---
### 소스 다운로드
fetch --nohooks webrtc_android

gclient sync
네트워크에 따라 몇 시간 걸림
중간에 라이센스 관련하여 y/n 을 물어본다.

---
### 필요라이브러리 설치
컴파일시 필요라이브러리 설치한다.
이는 최초 gclient sync 를 시행하고 그 다음에 수행한다.
폰트는 필요없으니 제외 옵션을 추가한다.
./build/install-build-deps.sh  --no-chromeos-fonts

./build/install-build-deps-android.sh

---
### 소스 빌드
* armeabi-v7a (arm 계열의 32비트)

gn gen out/Default --args='target_os="android" target_cpu="arm" is_debug=false'

ninja -C out/Default AppRTCMobile

* arm64-v8a (arm 계열의 64비트)

gn gen out_arm64/Default --args='target_os="android" target_cpu="arm64" is_debug=false'

ninja -C out_arm64/Default AppRTCMobile

* x86

gn gen out_x86/Default --args='target_os="android" target_cpu="x86" is_debug=false'

ninja -C out_x86/Default AppRTCMobile

* x64

gn gen out_x64/Default --args='target_os="android" target_cpu="x64" is_debug=false'

ninja -C out_x64/Default AppRTCMobile

안드로이드는 Arm V7 with Neon, Arm 64 두개만 하면 된다.
각각 지정한 폴더 밑으로 빌드본이 생긴다.
out/Default, out_arm64/Default

### so 파일 추출하기
so 파일을 추축하는 방법은 아래 두가지가 있다.
- 원본 so 파일 추출
[src]/out/Default/libjingle_peerconnection_so.so
- apk 에서 추출하기
[src]/out/Default/apks/AppRTCMobile.apk
압축 해제하면 libs 폴더가 존재하고 해당 폴더 안에 so 파일이 존재한다.


## 참고
아래 github 페이지에 CPU architecture 별로 만들어 놓은 library 가 있으니 참고하시기 바랍니다.
<https://github.com/jindotori/libjingle_peerconnection_so-android>
