# OpenCV_build_with_CUDA_on_Win10_VS2017

- with : eigen v3.3.7, tbb, cuda v10.2

- Download a pair of opencv and opencv_contrib. Version should be matched.

- Set proper CUDA_ARCH_BIN flag in CMAKE according to https://developer.nvidia.com/cuda-gpus
```
CUDA_ARCH_BIN 6.1 for GTX 1050 notebook
```

- Save cuda_runtime.h file as "UNICODE - CODE PAGE 1200" to remove "warning C4819" in VS2017
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime.h
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime_api.h
c:\program files\nvidia gpu computing toolkit\cuda\v10.2\include\sm_20_intrinsics.h
```
Reference : https://lucetewoo.tistory.com/15

- Set several CMake options

```
WITH_CUDA : ON
WITH_TBB : ON
WITH_EIGEN : ON

CUDA_ARCH_BIN : 6.1 

CUDA_HOST_COMPILER : C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/VC/Tools/MSVC/14.16.27023/bin/Hostx64/x64/cl.exe

TBB_DIR : <your_tbb_folder>/tbb/cmake
TBB_ENV_INCLUDE : <your_tbb_folder>/tbb/include/tbb
TBB_ENV_LIB : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb.lib
TBB_ENV_LIB_DEBUG : <your_tbb_folder>/tbb/lib/intel64/vc14/tbb_debug.lib

BUILD_opencv_world : ON
OPENCV_EXTRA_MODULES_PATH : <your_opencv_contrib_path>/modules

```
