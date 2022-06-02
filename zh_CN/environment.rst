.. DarkRISCV documentation master file, created by
   sphinx-quickstart on Wed Jun  1 09:55:02 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


操作系统要求
===================
推荐使用Ubuntu 16.04或以上版本。

安装交叉编译工具链
===================
DarkRISCV支持 ``riscv-gnu-toolchain`` 的最新版本。

在创建这个文档的时候最新版本是:
`commit:df6ecbe <https://github.com/riscv-collab/riscv-gnu-toolchain/tree/df6ecbe4ddb2a1a261b44af822d22f1253d3f0e4>`_ 。

**获取代码**

.. code-block:: shell

    git clone https://github.com/riscv/riscv-gnu-toolchain

**编译（NewLib）**

.. code-block:: shell

    ./configure --prefix=/opt/riscv32-gcc --with-arch=rv32gc --with-abi=ilp32d

    make

安装 Xilinx ISE
===================
**如果你还没开发板用于测试，你只是对DarkRISCV进项仿真学习的话，你可以不用安装ISE**

下载：
`Xilinx ISE 14.7 <https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive-ise.html>`_

建议安装到默认目录 **/opt** 目录。

安装完成之后使用以下命令使 ISE 生效：

.. code-block:: shell

    source /opt/Xilinx/14.7/ISE_DS/settings64.sh

安装其他工具
===================

**iverilog**

建议自己编译 iverilog，可以按照以下步骤进行：

.. code-block:: shell

    git clone https://github.com/steveicarus/iverilog.git
    cd iverilog
    # 切换到v10-branch分支，commits:b988543
    git checkout v10-branch
    autoreconf
    ./configure --prefix=/opt/iverilog-install
    make
    export PATH=$PATH:/opt/iverilog-install/bin/

.. warning:: 

    ISE 和 iverilog 可能存在冲突的情况，所以不建议使用 apt 直接安装 iverilog 到系统，
    而是编译完成后，像使用 ISE 一样，在需要的时候临时添加到环境变量。

**GTKWave**

.. code-block:: shell

    sudo apt-get install gtkwave






