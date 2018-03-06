# colab-for-ccminer
1.https://wiki.tiker.net/OpenCLHowTo
========================================
Debian
Debian packages OpenCL very well and makes installing this much easier.

Packages of ICD loaders: (you just need one of these)
-------------------------------------------------------

amd-libopencl1 (recommended)

nvidia-libopencl1

ocl-icd-libopencl1 (the reference implementation)

Packages of ICDs:
-------------------
amd-opencl-icd

nvidia-opencl-icd

beignet

Package for headers:
------------------------
opencl-headers

I would recommend using the latest versions (perhaps from the 'experimental' repository). Those are usually the least buggy.

In particular, Debian makes it straightforward to use both AMD and Nvidia GPUs in the same computer. Just let the AMD driver drive the display, for Nvidia only install the ICD.

The Intel CPU ICD is not packaged. Install it manually as above.

beignet is a project initiated by Intel to provide OpenCL support for their Ivy Bridge GPUs.

Tips and Tricks
Per-user ICD registry?
It's sometimes annoying that /etc/OpenCL/vendors is system-wide, i.e. individual users cannot install their own OpenCL ICDs. Here's a workaround.

Extract the AMD ICD (and ICD loader) as above, somewhere in your home directory.
Link against that libOpenCL.so when building your code.

Set LD_LIBRARY_PATH so that this libOpenCL.so gets picked up.

Make a new directory with a few .icd files as described above.

Set the environment variable OPENCL_VENDOR_PATH to that path.


Downloading the OpenCL headers
If you would also like the OpenCL headers, do the following:


TGT_DIR=/opt/opencl-headers/include/CL
mkdir -p $TGT_DIR && cd $TGT_DIR
wget https://raw.githubusercontent.com/KhronosGroup/OpenCL-Headers/master/opencl22/CL/{opencl,cl_platform,cl,cl_ext,cl_gl,cl_gl_ext}.h
Related Resources
Michael Hruby's guide to OpenCL on Ubuntu

Testing

apt-get install clinfo

clinfo

Number of platforms                               1
  Platform Name                                   NVIDIA CUDA
  Platform Vendor                                 NVIDIA Corporation
  Platform Version                                OpenCL 1.2 CUDA 8.0.0
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll cl_nv_copy_opts
  Platform Extensions function suffix             NV

  Platform Name                                   NVIDIA CUDA
Number of devices                                 1
  Device Name                                     Tesla K80
  Device Vendor                                   NVIDIA Corporation
  Device Vendor ID                                0x10de
  Device Version                                  OpenCL 1.2 CUDA
  Driver Version                                  375.26
  Device OpenCL C Version                         OpenCL C 1.2
  Device Type                                     GPU
  Device Profile                                  FULL_PROFILE
  Device Topology (NV)                            PCI-E, 00:03.6
  Max compute units                               13
  Max clock frequency                             823MHz
  Compute Capability (NV)                         3.7
  Device Partition                                (core)
    Max number of sub-devices                     1
    Supported partition types                     None
  Max work item dimensions                        3
  Max work item sizes                             1024x1024x64
  Max work group size                             1024
  Preferred work group size multiple              32
  Warp size (NV)                                  32
  
 2.https://www.cnblogs.com/kluan/p/6027490.html
 ================================================


# 1. 安装GO

sudo apt-get install golang-go
# 2. 设置Go环境变量

 打开终端，输入命令：

export GOROOT=$HOME/go
export PATH=$GOROOT/bin:$PATHU
# 3. 设置go代码目录

sudo mkdir Applications/go
# 4.  测试安装

完成安装后，新建一个文档来测试环境是否搭建成功:

Example helloWorld.go

复制代码
package main
 
    import (
        "fmt"
         "runtime"
    )

    func main() {
        fmt.Println("Hellow World!", runtime.Version())
    }    
复制代码
执行go run helloWorld.go, 应该会打印出：

或者go build helloWorld.go，将生成helloWorld.sh，./helloWorld也可以运行。

Hellow World! %!(EXTRA string=go1.6.2)
