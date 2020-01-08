# OpenCV_build_with_CUDA_on_Win10_VS2017


- Set proper CUDA_ARCH_BIN flag in CMAKE according to https://developer.nvidia.com/cuda-gpus
```
CUDA_ARCH_BIN 6.1 for GTX 1050 notebook
```

- Save cuda_runtime.h file as "UNICODE - CODE PAGE 1200" to remove "warning C4819" in VS2017
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2\include\cuda_runtime.h
```
Reference : https://lucetewoo.tistory.com/15
