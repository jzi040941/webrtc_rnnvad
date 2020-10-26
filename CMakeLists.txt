CMAKE_MINIMUM_REQUIRED(VERSION 3.9)
PROJECT(webrtc_rnnvad)

SET(CMAKE_CXX_STANDARD 11)
#ADD_DEFINITIONS(-g)

set(LINKLIBS)
set(COMPILE_OPTION)
set(INCL)
set(SRC)
add_definitions(-D_WINSOCKAPI_ -DWEBRTC_WIN -g -D_USE_MATH_DEFINES)

# Process Abseil's CMake build system
add_subdirectory(absl)

list(APPEND SRC
  src/main.cpp
  
  src/SRP_Wrapper.h
  src/SRP_Wrapper.cpp
  src/VadBuffer.h
  src/VadBuffer.cpp

  src/util/RT_Input.cpp
  src/util/RT_Input.h
  src/util/RT_Base.cpp
  src/util/RT_Base.h
  src/util/RT_Output.cpp
  src/util/RT_Output.h

  src/SRP_DSB.h
  src/FaceAnnotation.hpp
  src/FaceDetectOpencv.h

  src/Widgets/Wbase.h
  src/Widgets/Wbase.cpp
  src/Widgets/WDisplay.h
  src/Widgets/WDisplay.cpp
  src/Widgets/WSpectrogram.h
  src/Widgets/WSpectrogram.cpp  
  src/Widgets/KWebcam.h
  src/Widgets/Kwebcam.cpp  
  include/WAV/WAV.cpp
  
  #include/api
  #include/common_audio
  #include/rtc_base
  #include/modules
  include/common_audio/resampler/push_sinc_resampler.h
  include/common_audio/resampler/push_sinc_resampler.cc
  include/common_audio/resampler/sinc_resampler.h
  include/common_audio/resampler/sinc_resampler.cc
  include/rtc_base/checks.h
  include/rtc_base/checks.cc
  include/common_audio/include/audio_util.h
  include/common_audio/audio_util.cc
  include/modules/audio_processing/agc2/rnn_vad/features_extraction.h
  include/modules/audio_processing/agc2/rnn_vad/features_extraction.cc
  include/modules/audio_processing/agc2/rnn_vad/common.h
  include/modules/audio_processing/agc2/rnn_vad/common.cc
  include/modules/audio_processing/agc2/rnn_vad/rnn.h
  include/modules/audio_processing/agc2/rnn_vad/rnn.cc
include/modules/audio_processing/agc2/biquad_filter.cc
include/modules/audio_processing/agc2/biquad_filter.h
  include/third_party/rnnoise/src/rnn_activations.h
  include/third_party/rnnoise/src/rnn_vad_weights.h
  include/third_party/rnnoise/src/rnn_vad_weights.cc
  include/rtc_base/memory/aligned_malloc.h
include/rtc_base/memory/aligned_malloc.cc
include/modules/audio_processing/agc2/rnn_vad/pitch_info.h
include/modules/audio_processing/agc2/rnn_vad/pitch_search.h
include/modules/audio_processing/agc2/rnn_vad/pitch_search.cc
include/modules/audio_processing/agc2/rnn_vad/sequence_buffer.h
include/modules/audio_processing/agc2/rnn_vad/spectral_features.h
include/modules/audio_processing/agc2/rnn_vad/spectral_features.cc
include/modules/audio_processing/agc2/rnn_vad/lp_residual.h
include/modules/audio_processing/agc2/rnn_vad/lp_residual.cc
include/modules/audio_processing/agc2/rnn_vad/auto_correlation.h
include/modules/audio_processing/agc2/rnn_vad/auto_correlation.cc
include/modules/audio_processing/agc2/rnn_vad/pitch_search_internal.h
include/modules/audio_processing/agc2/rnn_vad/pitch_search_internal.cc
include/modules/audio_processing/agc2/rnn_vad/spectral_features.h
include/modules/audio_processing/agc2/rnn_vad/spectral_features.cc
include/modules/audio_processing/agc2/rnn_vad/spectral_features_internal.h
include/modules/audio_processing/agc2/rnn_vad/spectral_features_internal.cc
include/modules/audio_processing/agc2/rnn_vad/ring_buffer.h
include/modules/audio_processing/agc2/rnn_vad/symmetric_matrix_buffer.h
include/modules/audio_processing/utility/pffft_wrapper.h
include/modules/audio_processing/utility/pffft_wrapper.cc
include/third_party/pffft/src/pffft.h
include/third_party/pffft/src/pffft.c
include/third_party/pffft/src/fftpack.h
include/third_party/pffft/src/fftpack.c
ADD_LIBRARY(webrtc_rnnvad SHARED ${VAD_SOURCE_FILES})
TARGET_LINK_LIBRARIES(webrtc_rnnvad pthread)
ADD_DEPENDENCIES(webrtc_rnnvad copy_header)

INCLUDE_DIRECTORIES(
    ${PROJECT_SOURCE_DIR}
)

LINK_DIRECTORIES(
    ${LIBRARY_OUTPUT_PATH}
)

ADD_EXECUTABLE(main main.cc)
TARGET_LINK_LIBRARIES(main webrtc_rnnvad)
