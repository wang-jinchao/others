#CUDA cuDNN  
===

|Version|CPU/GPU|Python Version|Compiler|Build Tools|cuDNN|CUDA|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|tensorflow_gpu-1.7.0|GPU|2.7|3.3-3.6|	GCC 4.8|Bazel 0.9.0|7|9|

<pre>
<em>#cuda 版本:</em>
<strong>[wangjinchao@gpu1 ~]$ cat /usr/local/cuda/version.txt</strong>
CUDA Version 8.0.44

<em>#cudnn 版本:</em> 
<strong>[wangjinchao@gpu1 ~]$ cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2</strong>
#define CUDNN_MAJOR      5
#define CUDNN_MINOR      1
#define CUDNN_PATCHLEVEL 5

#define CUDNN_VERSION    (CUDNN_MAJOR * 1000 + CUDNN_MINOR * 100 + CUDNN_PATCHLEVEL)

#include "driver_types.h"

<em>#Linux 内核版本:</em>
<strong>[wangjinchao@gpu1 myproject]$ cat /proc/version</strong>
Linux version 3.10.0-514.26.2.el7.x86_64 (builder@kbuilder.dev.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-11) (GCC) ) #1 SMP Tue Jul 4 15:04:05 UTC 2017

<em>Linux 系统版本的命令:</em>
<strong>[wangjinchao@gpu1 myproject]$ lsb_release -a</strong>
LSB Version:    :core-4.1-amd64:core-4.1-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-4.1-amd64:desktop-4.1-noarch:languages-4.1-amd64:languages-4.1-noarch:printing-4.1-amd64:printing-4.1-noarch
Distributor ID: CentOS
Description:    CentOS Linux release 7.3.1611 (Core)
Release:        7.3.1611
Codename:       Core
</pre>

<pre>
[root@gpu1:/usr/local]
# cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  384.98  Thu Oct 26 15:16:01 PDT 2017
GCC version:  gcc 版本 4.8.5 20150623 (Red Hat 4.8.5-11) (GCC)




</pre>

<em>#检测cuda是否安装成功:</em>

    cd /usr/local/cuda-8.0/samples/1_Utilities/deviceQuery 
    make -j4  
    sudo ./deviceQuery  
