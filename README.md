# OpenCV_build_with_CUDA_on_Win10_VS2017

- with : eigen v3.3.7, tbb, cuda v10.2

- tbb v2020 only support Visual Studio 2017(vc14)
- tbb v2017 supports Visual Studio 2013, 2015, 2017

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
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda.h
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

- General configuration for OpenCV 4.1.1

```
  Version control:               unknown

  Extra modules:
    Location (extra):            C:/opencv-4.1.1/opencv_contrib-4.1.1/modules
    Version control (extra):     unknown

  Platform:
    Timestamp:                   2020-01-08T01:45:50Z
    Host:                        Windows 10.0.18362 AMD64
    CMake:                       3.16.0-rc2
    CMake generator:             Visual Studio 15 2017
    CMake build tool:            C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/MSBuild/15.0/Bin/MSBuild.exe
    MSVC:                        1916

  CPU/HW features:
    Baseline:                    SSE SSE2 SSE3
      requested:                 SSE3
    Dispatched code generation:  SSE4_1 SSE4_2 FP16 AVX AVX2 AVX512_SKX
      requested:                 SSE4_1 SSE4_2 AVX FP16 AVX2 AVX512_SKX
      SSE4_1 (13 files):         + SSSE3 SSE4_1
      SSE4_2 (1 files):          + SSSE3 SSE4_1 POPCNT SSE4_2
      FP16 (0 files):            + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 AVX
      AVX (4 files):             + SSSE3 SSE4_1 POPCNT SSE4_2 AVX
      AVX2 (27 files):           + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 FMA3 AVX AVX2
      AVX512_SKX (2 files):      + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 FMA3 AVX AVX2 AVX_512F AVX512_COMMON AVX512_SKX

  C/C++:
    Built as dynamic libs?:      YES
    C++ Compiler:                C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/VC/Tools/MSVC/14.16.27023/bin/Hostx86/x64/cl.exe  (ver 19.16.27034.0)
    C++ flags (Release):         /DWIN32 /D_WINDOWS /W4 /GR  /D _CRT_SECURE_NO_DEPRECATE /D _CRT_NONSTDC_NO_DEPRECATE /D _SCL_SECURE_NO_WARNINGS /Gy /bigobj /Oi  /fp:precise     /EHa /wd4127 /wd4251 /wd4324 /wd4275 /wd4512 /wd4589 /MP8   /MD /O2 /Ob2 /DNDEBUG 
    C++ flags (Debug):           /DWIN32 /D_WINDOWS /W4 /GR  /D _CRT_SECURE_NO_DEPRECATE /D _CRT_NONSTDC_NO_DEPRECATE /D _SCL_SECURE_NO_WARNINGS /Gy /bigobj /Oi  /fp:precise     /EHa /wd4127 /wd4251 /wd4324 /wd4275 /wd4512 /wd4589 /MP8   /MDd /Zi /Ob0 /Od /RTC1 
    C Compiler:                  C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/VC/Tools/MSVC/14.16.27023/bin/Hostx86/x64/cl.exe
    C flags (Release):           /DWIN32 /D_WINDOWS /W3  /D _CRT_SECURE_NO_DEPRECATE /D _CRT_NONSTDC_NO_DEPRECATE /D _SCL_SECURE_NO_WARNINGS /Gy /bigobj /Oi  /fp:precise       /MP8    /MD /O2 /Ob2 /DNDEBUG 
    C flags (Debug):             /DWIN32 /D_WINDOWS /W3  /D _CRT_SECURE_NO_DEPRECATE /D _CRT_NONSTDC_NO_DEPRECATE /D _SCL_SECURE_NO_WARNINGS /Gy /bigobj /Oi  /fp:precise       /MP8  /MDd /Zi /Ob0 /Od /RTC1 
    Linker flags (Release):      /machine:x64  /INCREMENTAL:NO 
    Linker flags (Debug):        /machine:x64  /debug /INCREMENTAL 
    ccache:                      NO
    Precompiled headers:         NO
    Extra dependencies:          cudart.lib C:/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v10.2/lib/x64/cuda.lib nppc.lib nppial.lib nppicc.lib nppicom.lib nppidei.lib nppif.lib nppig.lib nppim.lib nppist.lib nppisu.lib nppitc.lib npps.lib cublas.lib cufft.lib -LIBPATH:C:/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v10.2/lib/x64
    3rdparty dependencies:

  OpenCV modules:
    To be built:                 aruco bgsegm bioinspired calib3d ccalib core cudaarithm cudabgsegm cudacodec cudafeatures2d cudafilters cudaimgproc cudalegacy cudaobjdetect cudaoptflow cudastereo cudawarping cudev datasets dnn dnn_objdetect dpm face features2d flann fuzzy gapi hfs highgui img_hash imgcodecs imgproc line_descriptor ml objdetect optflow phase_unwrapping photo plot quality reg rgbd saliency shape stereo stitching structured_light superres surface_matching text tracking video videoio videostab world xfeatures2d ximgproc xobjdetect xphoto
    Disabled:                    -
    Disabled by dependency:      -
    Unavailable:                 cnn_3dobj cvv freetype hdf java js matlab ovis python2 python3 sfm ts viz
    Applications:                examples apps
    Documentation:               NO
    Non-free algorithms:         YES

  Windows RT support:            NO

  GUI: 
    Win32 UI:                    YES

  Media I/O: 
    ZLib:                        build (ver 1.2.11)
    JPEG:                        build-libjpeg-turbo (ver 2.0.2-62)
    WEBP:                        build (ver encoder: 0x020e)
    PNG:                         build (ver 1.6.37)
    TIFF:                        build (ver 42 - 4.0.10)
    JPEG 2000:                   build (ver 1.900.1)
    OpenEXR:                     build (ver 2.3.0)
    HDR:                         YES
    SUNRASTER:                   YES
    PXM:                         YES
    PFM:                         YES

  Video I/O:
    FFMPEG:                      YES (prebuilt binaries)
      avcodec:                   YES (58.35.100)
      avformat:                  YES (58.20.100)
      avutil:                    YES (56.22.100)
      swscale:                   YES (5.3.100)
      avresample:                YES (4.0.0)
    DirectShow:                  YES
    Media Foundation:            YES
      DXVA:                      YES

  Parallel framework:            TBB (ver 2020.0 interface 11100)

  Trace:                         YES (with Intel ITT)

  Other third-party libraries:
    Intel IPP:                   2019.0.0 Gold [2019.0.0]
           at:                   C:/opencv-4.1.1/build/3rdparty/ippicv/ippicv_win/icv
    Intel IPP IW:                sources (2019.0.0)
              at:                C:/opencv-4.1.1/build/3rdparty/ippicv/ippicv_win/iw
    Lapack:                      NO
    Eigen:                       YES (ver 3.3.7)
    Custom HAL:                  NO
    Protobuf:                    build (3.5.1)

  NVIDIA CUDA:                   YES (ver 10.2, CUFFT CUBLAS FAST_MATH)
    NVIDIA GPU arch:             61
    NVIDIA PTX archs:

  cuDNN:                         NO

  OpenCL:                        YES (NVD3D11)
    Include path:                C:/opencv-4.1.1/3rdparty/include/opencl/1.2
    Link libraries:              Dynamic load

  Python (for build):            C:/Python36/python.exe

  Install to:                    C:/opencv-4.1.1/install
  ```
