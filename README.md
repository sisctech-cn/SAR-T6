SAR-T6
=====================
（Simplified and Advanced RISC CPU： T6）

# 介绍
“飒”是由北京芯启科技有限公司（SiSCTECHnology CO.,LTD）所开发IP的总体代号，基于“飒”为核心模块，我们还提供芯片SoC架构“靖”级别的设计服务，以及进一步提供端侧的PCBA硬件方案。

其中T6是一款低功耗RISC CPU IP，支持在其基础架构上进行灵活多样的精简或扩展开发设计服务。例如，基于多个T6 CPU构成的众核或者簇设计可以构成CPU阵列，或者基于T6搭配硬件算子可以提供出高效的专用计算加速器。

在此我们将T6基础型号的C model开放上来，它是对应该IP基础型号的硬件RTL设计实现的一个C语言模型，具有功能一致且有时钟精确度的特点，可以作为模拟器使用，便于所有人下载、评估，您可基于此model修改使之构成您的统一软硬件调试环境，推动您的系统开发进程。

该T6基础型号的特征为：
+ 兼容RISC-V指令集
+ 32位
+ 3级流水线
+ 1.4 DMIPS/MHz


# 运行说明
C model操作流程，便于上手运行。

在release目录中，有压缩打包好的发布文件包sisc_d9_cmodel_*.tgz

目录结构：
-----------
    ├── release                 #   
    │   ├── *.tgz               # package for public
    |   |   ├── dpram           # CPU Micro Arch. :
    |   |   ├── AHBram32b       #   CPU T6 + bus + I/D TCM
    |   |   ├── dhry            # the source code of dhrystone + a user top.c demo
    |   |   ├── sisc32_core     # T6 C model source code
    |   |   ├── run             # run script
    |   |   ├── testsc.cpp      # main program that calls the C model
    |   |   ├── top.hex         # machine code of Dhrystone demo
    |   ├── SISC_T6-run_manual.docx
    ├── README.md                                 
    ├── LICENSE                                   

环境：
-----------
在linux服务器上运行,运行和结果信息都将在屏幕输出。

为了调用SAR-T6 C model，我们用SystemC语言编写了一个简明的CPU微架构测试平台。当将平台与C model一起编译链接的时候，您要依赖以下内容：
+ 开源的GNU，在脚本中调用的是GNU 4.8.5
+ 开源的[Verilator库](https://www.veripool.org/wiki/verilator)
+ 开放的[SystemC库2.3.3](https://www.accellera.org/downloads/standards/systemc)

在评估代码中有Dhrystone测试代码，已编译为处理器可执行的机器码，可以被 C model直接载入、模拟硬件执行行为。
如果您还想调试其他用户C程序，您需要软件工具链。您可通过开源的RISC-V的GCC编译器自行获得，或联系芯启科技购买相关技术支持。

设置：
-----------

步骤：
-----------
您可直接下载sisc_t6_cmodel_20190412.tgz

    $ tar -xzf sisc_t6_cmodel_20190412.tgz
    $ cd sisc_t6_cmodel_20190412/cmodel
    
您需要编辑run脚本，设置GNU、verilator和SystemC的本地路径后直接执行

    $ run

结果请参考release/SISC_T6-run_manual.docx文档末尾的屏幕输出示意图。testcase会自动计算当前CPU和微架构环境下的性能测算结果。

微信公众号：北京芯启科技
