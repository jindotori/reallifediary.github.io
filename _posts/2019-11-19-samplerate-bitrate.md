---
title: 샘플레이트(Sample rate), 비트(Bit), 비트레이트(Bit rate)
layout: post
summary: 샘플레이트, 비트, 비트레이트 알아보기
categories: multimedia
---
자꾸 까먹고 다른 좋은 글들을 읽으면 이해력도 좀 딸려서 나름 이해한 걸 정리해 봤습니다.
물론 틀리거나 정확치 않은 내용도 있을지도 모릅니다. 감안하시구요.
더 자세한 건 다른 분들의 글을 참고하시면 될 겁니다.

## 순서
   1. 주파수와 진폭   2. 샘플레이트, 비트   3. 샘플레이트   4 비트    5. 비트레이트

#### 주파수와 진폭
frequency(Hz), amplitude(dB)

음악은 공기의 진동으로 이루어지기 때문에 진폭(음량), 주파수(고저음)로 이루어집니다.

아래 그림으로 보자면 세로로 더 높게 진동하면 소리가 커지겠고
좌우(시간축)을 따라 더 많이 빨리 진동하면 주파수가 높아져 높은 음이 날 겁니다.

![Samplerate](https://t1.daumcdn.net/cfile/tistory/995F6A495B67C35132)

위 곡선과 같은 아날로그 음이 있다 할 때 이 소리를 디지탈로 재현하려면
학교시절 수학에서 미적분하듯이 수없이 쪼개서 원값에 가깝게 만들어야 합니다.

#### 샘플레이트와 비트(심도)

Sample Rate, Bit Depth
이때 정확도를 높이려면 가로로도 쪼개야 하고 세로로도 쪼개야 하는데,
여기서 가로는 Sample Rate, 세로는 Bit Depth가 됩니다.

![samplerateandbit](https://t1.daumcdn.net/cfile/tistory/997DF24A5B67C20D28)

둘다 많이 쪼갤 수록 아날로그 신호에 접근하게 됩니다.

![sampleratebitdepth](https://t1.daumcdn.net/cfile/tistory/99832C425B67CBB729)

#### 샘플레이트 (Sample Rate)

가로(주파수)를 많이 쪼갤수록 아날로그 신호의 곡선에 접근함을 할 수 있습니다.
보통 44100Hz(44.1kHz), 48000Hz(48kHz) 등 용어가 샘플레이트에 해당됩니다.

즉 1초에 4만4천의 샘플(44100Hz)을 찍어 그 값을 알게 되면 아무래도 2만개 샘플로 추출한 값보다는 훨씬 정확하겠죠

![bitdepth](https://t1.daumcdn.net/cfile/tistory/992F333E5B67C67C22)

#### 비트(심도) (Beat Depth)



위 그림 왼쪽 부분 bit depth와 세로줄 몇개는 원 그림에 제가 덧칠을 했는데

샘플레이트만 높고 비트레이트가 낮으면 여전히 아날로그 음을 충분히 재현하지 못합니다. 즉 음량에서 왜곡이 일어나니 전체적으로 음이 왜곡되겠지요. 아래 그림을 보면 전체적으로 이해가 되실 겁니다.

위 샘플레이트의 4만4천개 샘플에서 1개 샘플 당 16비트라는 정보를 가지는 것보다는 24비트가 더 정확하게 표현될 수 있을 겁니다. 굳이 비유하자면, 모니터의 한 화소 더 많은 색 정보를 가지고 있다면 당연히 색이 더 고와지겠죠.


보통 16비트, 24비트 32비트 하는 것이 비트 심도를 일컫는 용어입니다.

![bitdepth2](https://t1.daumcdn.net/cfile/tistory/99224A3E5B67C67C23)

#### 비트레이트 (Bit Rate)

우선 비트레이트는 흔히 mp3의 128kbit/s, 192 kbit/s 등 처럼 음질과 관련되어 있습니다.



       비트레이트 = 샘플레이트 X 비트(심도) X 채널



위 공식처럼 샘플레이트와 비트가 높아지면 mp3 음질이 좋아지게 마련입니다. 반대의 경우는 거칠구요.
그러니 음악 제작할 때 셈플레이트, 비트 심도가 당연히 중요합니다.
그러나 너무 높으면 파일 크기가 너무 커질수도 있고 노이즈가 들어간다든지 문제도 있다고 합니다만
대체로 샘플레이트가 높으면 음질이 좋아지고 레이턴시가 줄어든다고 합니다.


여기서 채널은 모노(1)나 스테레오 2채널, 2.1채널, 5채널 같은 얘기와 같이 스피커 수를 말합니다.
즉 디지탈 신호 안에 이미 어느 소리를 어떤 귀나 스피커로 보낼지 분리가 되어 있는 거죠.

<출처>
<https://tadream.tistory.com/25365>
