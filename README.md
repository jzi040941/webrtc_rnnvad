# WebRTC RNN VAD (RNNoise VAD)
Recurrent Neural Network Voice activity detection (RNN VAD) example project, extract from WebRTC.

This repository just contains the scripts to test RNN VAD library from WebRTC source code.  

[1]https://webrtc.org/
[2]https://jmvalin.ca/demo/rnnoise/
## Building

1. Get Abseil-cpp source code
```
git submodule update --recursive --remote
```

2. Build with cmake
```
mkdir bin
cmake ..
make
```

## Usage
you need wav file which is 16khz sample rate for test RNNVAD

```
main.exe -i test.wav -f features.file -o vadprob.file
```
