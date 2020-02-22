# OpenCV_build_with_CUDA_on_Win10_VS2017

- with : tbb, cuda

- Download tbb :
https://github.com/intel/tbb/releases

- Download a pair of opencv and opencv_contrib. Version should be matched.

- Set proper CUDA_ARCH_BIN flag in CMAKE according to https://developer.nvidia.com/cuda-gpus
```
CUDA_ARCH_BIN 6.1 for GTX 1050 notebook / GTX 1080 Ti
```

- (Options) Save cuda_runtime.h file as "UNICODE - CODE PAGE 1200" to remove "warning C4819" in VS2017
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime_api.h
c:\program files\nvidia gpu computing toolkit\cuda\v10.2\include\sm_20_intrinsics.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda.h
```
Reference : https://lucetewoo.tistory.com/15

- Set several CMake options

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


WITH_1394 : OFF

```
- CUDA options

```
CUDA_ARCH_BIN : 6.1 
```

- TBB options

```
TBB_DIR : <your_tbb_folder>/tbb/cmake
TBB_ENV_INCLUDE : <your_tbb_folder>/tbb/include/tbb
TBB_ENV_LIB : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb.lib
TBB_ENV_LIB_DEBUG : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb_debug.lib
```

- NVIDIA Video Codec SDK 2.1
developer.nvidia.com/nvidia-video-codec-sdk/download#NVDECFeatures

```
CUDA_nvcuvid_LIBRARY : <install path>Lib/x64/nvcuvid.lib
```



# stitching_detailed.cpp with CUDA

https://answers.opencv.org/question/95148/cudalegacy-not-compile-nppigraphcut-missing/

