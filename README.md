# WebRTC RNN VAD (RNNoise VAD)
Recurrent Neural Network Voice activity detection (RNN VAD) example project, extract from WebRTC.

This repository just contains the scripts to test RNN VAD library from WebRTC source code.  

[1]https://webrtc.org/
[2]https://jmvalin.ca/demo/rnnoise/
## Building

1. Get Abseil-cpp source code
```
git clone https://github.com/abseil/abseil-cpp.git
```

2. Build with cmake
```
mkdir bin
cmake ..
```

## Usage
you need wav file which is 16khz sample rate for test RNNVAD

```
webrtc_rnnvad.exe -i test.wav -f features.file -o vadprob.file
```
