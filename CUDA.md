# CUDA--cuDNN    

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


<pre>
Install nvidia driver：

    https://developer.nvidia.com/cuda-90-download-archive?target_os=Linux&target_arch=x86_64&target_distro=CentOS&target_version=7&target_type=runfilelocal
    
    [wangjinchao@gpu1 ~]$ wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run

======

    chmod +x cuda_8.0.61_375.26_linux-run
    mkdir nvidia_installers
    ./cuda_8.0.61_375.26_linux-run -extract=`pwd`/nvidia_installers
    cd nvidia_installers
    ./NVIDIA-Linux-x86_64-375.26.run --kernel-source-path=/usr/src/kernels/linux/

    sudo chmod 755 cuda_5.0.35_linux_64_ubuntu11.10-1.run  
    sudo ./cuda_5.0.35_linux_64_ubuntu11.10-1.run  


    Install CUDA
    ./cuda-linux64-rel-8.0.61-21551265.run


    sudo chmod +x cuda_9.0.176_384.81_linux.run # 为 cuda_9.0.176_384.81_linux.run 添加可执行权限
    ./cuda_9.0.176_384.81_linux.run # 安装 cuda_9.0.176_384.81_linux.run



    suda sh cuda-9.1.run --silent --toolkit --toolkitpath=/usr/local/cuda-9.1

=======

Verify CUDA
    ./cuda-samples-linux-8.0.61-21551265.run
    cd /usr/local/cuda/samples/1_Utilities/deviceQuery
    make
    ./deviceQuery
Set Path
    export PATH=$PATH:/usr/local/cuda-8.0/bin
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-8.0/lib64

###  Base Installer	
    Installation Instructions:
    Run `sudo sh cuda_9.0.176_384.81_linux.run`
    Follow the command-line prompts

</pre>


这样Cuda8 和Cuda9 就同时安装在服务器上了； 你可以在在shell文件中切换，也可以修改/usr/local/cuda的符号链接

  


===========
= Summary =
===========

Driver:   Not Selected
Toolkit:  Installed in /media/cuda-9.0
Samples:  Installed in /media/cuda-9.0/Samples, but missing recommended libraries

Please make sure that
 -   PATH includes /media/cuda-9.0/bin
 -   LD_LIBRARY_PATH includes /media/cuda-9.0/lib64, or, add /media/cuda-9.0/lib64 to /etc/ld.so.conf and run ldconfig as root

To uninstall the CUDA Toolkit, run the uninstall script in /media/cuda-9.0/bin

Please see CUDA_Installation_Guide_Linux.pdf in /media/cuda-9.0/doc/pdf for detailed information on setting up CUDA.

***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 384.00 is required for CUDA 9.0 functionality to work.
To install the driver using this installer, run the following command, replacing <CudaInstaller> with the name of this run file:
    sudo <CudaInstaller>.run -silent -driver

Logfile is /tmp/cuda_install_2955.log
