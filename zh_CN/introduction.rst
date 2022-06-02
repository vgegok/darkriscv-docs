.. DarkRISCV documentation master file, created by
   sphinx-quickstart on Wed Jun  1 09:55:02 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

介绍
===================

DarkRISCV软核是在 2018 年 8 月 19 日的一个神奇之夜凌晨 2 点到 8 点之间开发的， 最初是作为开源 RISC-V 指令集的概念证明。

**尽管与其他 RISC-V 实现相比，代码小而粗糙，但DarkRISCV具有许多令人印象深刻的特性：**

- 实现了大部分 RISC-V RV32E 指令集
- 实现了大部分 RISC-V RV32I 指令集（缺少 csr*、e* 和 fence*）
- 在超大规模 ku040 中工作频率高达 250MHz（400MHz w/ 超频！）
- 在便宜的 spartan-6 中高达 100MHz，适合小型 spartan-3E，例如 XC3S100E！
- 大部分时间可以维持每条指令 1 个时钟（通常是 71% 的时间）
- 灵活的哈佛架构（易于集成缓存控制器、总线桥等）
- 在真正的 xilinx（spartan-3、spartan-6、spartan-7、artix-7、kintex-7 和 kintex ultrascale）中运行良好
- 与一些真正的 altera 和 lattice FPGA 一起工作得很好
- 适用于 RISC-V 的 gcc 9.0.0以上版本的交叉编译器（无需补丁！）
- 使用 850-1500LUTs（仅核心采用 LUT6 技术，取决于启用的功能和优化）
- 可选的 RV32E 支持（与 LUT4 FPGA 配合使用效果更好）
- 可选 16x16 位 MAC 指令（用于数字信号处理）
- 可选粗粒度多线程 (MT)
- 管道阶段之间没有互锁！
- BSD许可证：可以在任何地方使用，没有任何限制！
  
**一些额外的功能计划在未来或正在开发中：**

- 中断控制器（测试中）
- 缓存控制器（测试中）
- gpio 和计时器（正在测试中）
- 带数据扰频器的 sdram 控制器
- 分支预测器（测试中）
- 以太网控制器 (GbE)
- 多处理 (SMP)
- 片上网络 (NoC)
- rv64i 支持（不像看起来那么容易......）
- 动态总线大小和大端支持
- 用户/主管模式
- 调试支持
- 未对齐的内存访问
- 用于 8/16/32 位总线的桥接器
- 还有许多其他功能！

目录结构
===================

虽然DarkRISCV只是一个小型处理器内核，但需要一个小型生态系统来测试内核，包括 RISCV 兼容软件、对模拟的支持和对外围设备的支持，以使处理器内核产生可观察的结果。

每个元素都与目录中的相似元素一起存储，顶层具有以下组织：

=============  ========================================================
**rtl**        DarkRISCV核心和支持逻辑的源代码(Verilog)
**src**        DarkRISCV应用层代码
**sim**        用于测试 rtl 文件的模拟源代码（目前通过 icarus）
**boards**     不同开发板的支持和示例（目前通过 Xilinx ISE）
**docs**       本文档的源代码目录
**tmp**        默认为空文件夹，但 ISE 会在此处创建大量文件
**Makefile**   顶层Makefile
**README.md**  顶层自述文件
**LICENSE**    BSD 3-Clause "New" or "Revised" License，没有任何限制
=============  ========================================================


支持的开发板
===================

====  ================================  ===========================
ID    在DarkRISCV中的名称                FPGA厂商/开发工具
====  ================================  ===========================
0     **simulation only**               仿真输出的board名称   
1     **avnet_microboard_lx9**          Xilinx/ISE
2     **xilinx_ac701_a200**             Xilinx
3     **qmtech_sdram_lx16**             Xilinx/ISE
4     **qmtech_spartan7_s15**           Xilinx
5     **lattice_brevia2_lxp2**          Xilinx
6     **piswords_rs485_lx9**            Xilinx/ISE
7     **digilent_spartan3_s200**        Xilinx
8     **aliexpress_hpc40gbe_k420**      Xilinx
9     **qmtech_artix7_a35**             Xilinx
10    **aliexpress_hpc40gbe_ku040**     Xilinx
11    **papilio_duo_logicstart**        Xilinx
12    **qmtech_kintex7_k325**           Xilinx
13    **scarab_minispartan6-plus_lx9**  Xilinx/ISE
====  ================================  ===========================

.. note:: 
    更多开发板的支持在之后会不断添加，也欢迎读者添加常见的开发板支持到github上。

依赖的软件
===================

- `riscv-gnu-toolchain <https://github.com/riscv-collab/riscv-gnu-toolchain>`_ : RISC-V交叉编译工具链，可以使用最新版本
- `Xilinx ISE 14.7 <https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive-ise.html>`_ : Xilinx FPGA开发环境，生成下载到bit流文件
- `icarus Verilog <https://github.com/steveicarus/iverilog>`_ : 用于仿真和代码调试
- `GTKWave <https://github.com/gtkwave/gtkwave>`_ : 查看仿真波形




