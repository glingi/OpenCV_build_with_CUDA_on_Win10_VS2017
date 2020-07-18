# OpenCV_build_with_CUDA_on_Ubuntu_18.04

- CUDA installation : https://docs.nvidia.com/cuda/archive/10.0/cuda-installation-guide-linux/index.html

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
WITH_FFMPEG : ON

OPENCV_EXTRA_MODULES_PATH : <your_opencv_contrib_path>/modules
OPENCV_ENABLE_NONFREE : ON
OPENCV_GENERATE_PKGCONFIG : ON

ENABLE_FAST_MATH : ON

BUILD_opencv_world : ON
BUILD_TEST : OFF
BUILD_PERF_TEST : OFF
BUILD_PACKAGE : OFF
BUILD_opencv_cudacodec : ON (NVIDIA VIDEO CODEC SDK is requried)

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

- (Options) Save cuda_runtime.h file as "UNICODE - CODE PAGE 1200" to remove "warning C4819" in VS2017
  + Reference : https://lucetewoo.tistory.com/15
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime_api.h
c:\program files\nvidia gpu computing toolkit\cuda\v10.2\include\sm_20_intrinsics.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda.h
```
# Using CUDACODEC VIDEOREADER

OpenCV 4.x version basically does not support udacodec::VideoReader function. Additional steps are required to use cudacodec [1].

1. Download NVIDIA VIDEO CODEC SDK : https://developer.nvidia.com/nvidia-video-codec-sdk

2. After extracing zip file, copy all header files in <video_codec_sdk>/interface into both   1) /usr/local/cuda/include   and   2) /usr/local/cuda-10.0/include 

3. Check the system architecture
```
$ uname -a
Linux username 5.3.0-62-generic #56~18.04.1-Ubuntu SMP Wed Jun 24 16:17:03 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
4. Copy all library files in <video_codec_sdk>/Lib/linux/stubs/<architecture>  into both   1) /usr/local/cuda/lib64   and   2) /usr/local/cuda-10.0/lib64

5. In CMake, set WITH_NVCUVID = ON 

6. Build OpenCV

7. Run source code : https://github.com/opencv/opencv/blob/master/samples/gpu/video_reader.cpp

Refereces
[1] https://jamesbowley.co.uk/accelerate-opencv-4-2-0-build-with-cuda-and-python-bindings/

# stitching_detailed.cpp with CUDA

https://answers.opencv.org/question/95148/cudalegacy-not-compile-nppigraphcut-missing/

