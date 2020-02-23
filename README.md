# OpenCV_build_with_CUDA_on_Ubuntu_18.04

- Download
  + CMake : https://cmake.org/download/
  + Note ! : a pair of opencv and opencv_contrib version should be matched
  + OpenCV : https://github.com/opencv/opencv/releases
  + OpenCV Contrib : https://github.com/opencv/opencv_contrib/releases
  + CUDA (login needed) : https://developer.nvidia.com/cuda-toolkit-archive
  + CUDNN (login needed) : https://developer.nvidia.com/rdp/cudnn-archive
  + TBB : https://github.com/intel/tbb/releases
 
- Intall GTK (Only Ubuntu)
```
$ sudo apt-get install ffmpeg
$ sudo apt-get install libgtk2.0-dev
$ sudo apt-get install libavcodec-dev libavformat-dev libavdevice-dev
```

- Set CMake options

```
WITH_CUDA : ON
WITH_TBB : ON

OPENCV_EXTRA_MODULES_PATH : <your_opencv_contrib_path>/modules
OPENCV_ENABLE_NONFREE : ON
OPENCV_GENERATE_PKGCONFIG : ON

ENABLE_FAST_MATH : ON

BUILD_opencv_world : ON
BUILD_TEST : OFF
BUILD_PERF_TEST : OFF
BUILD_PACKAGE : OFF
BUILD_opencv_cudacodec : OFF (for CUDA 10 and OpenCV 3.4.2)

WITH_1394 : OFF

```

- CUDA options 
  + Check CUDA_ARCH_BIN in CMAKE here : https://developer.nvidia.com/cuda-gpus
```
CUDA_ARCH_BIN : 6.1 (for GTX 1050 notebook / GTX 1080 Ti / MX150)
```

- TBB options

```
TBB_DIR : <your_tbb_folder>/tbb/cmake
TBB_ENV_INCLUDE : <your_tbb_folder>/tbb/include/tbb
TBB_ENV_LIB : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb.lib
TBB_ENV_LIB_DEBUG : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb_debug.lib
```

- (Options) NVIDIA Video Codec SDK 2.1
developer.nvidia.com/nvidia-video-codec-sdk/download#NVDECFeatures

```
CUDA_nvcuvid_LIBRARY : <install path>Lib/x64/nvcuvid.lib
```



- (Options) Save cuda_runtime.h file as "UNICODE - CODE PAGE 1200" to remove "warning C4819" in VS2017
  + Reference : https://lucetewoo.tistory.com/15
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime_api.h
c:\program files\nvidia gpu computing toolkit\cuda\v10.2\include\sm_20_intrinsics.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda.h
```


# stitching_detailed.cpp with CUDA

https://answers.opencv.org/question/95148/cudalegacy-not-compile-nppigraphcut-missing/

