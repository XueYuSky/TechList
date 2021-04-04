# 第一章 EDA设计概述

## EDA技术三要素
EDA技术应用涉及硬件、软件和语言三个方面。

硬件实现载体： 可编程逻辑器件

设计平台： EDA设计软件

描述设计思想的工具： 硬件描述语言

---
### 可编程逻辑器件
可编程逻辑器件发展的四个阶段：
1. 20世纪70年代初到70年代中期，主要器件： PROM,EPROM和EEPROM。
2. 20世纪70年代中期到80年代中期，主要器件： PAG和GAL器件，内部主要由“与-或逻辑阵列”，同时集成少量**触发器**，构成PLD。
3. 20世纪80年代中期到90年代末期，主要器件：CPLD和FPGA。其中，FPGA具有结构灵活，集成度高等优点，成为产品原型设计的首选。
4. 20世纪90年代末至今，主要器件： 百万门级和千万门级的FPGA，同时内嵌硬件乘法器、硬核处理器和Gbits查分穿行接口等。----SOPC技术开始流行。

---
### 结构演进过程
1. 基于乘积项结构的PLD
2. 基于查找表结构的FPGA
---
### Intel 可编程逻辑器件常用列表

---
### Xilinx可编程逻辑器件常用列表

---
## 硬件描述语言
1. Verilog HDL
2. VHDL
3. SystemVerilog和SystemC
---
## EDA软件
### 集成开发环境
一、 Intel(Altera)集成开发环境

1. Quartus II 13.1 sp1 (学习与生产环境)
2. Quartus II 20 sp1 (学习环境)

二、 Xilinx集成开发环境
1. [ISE 14.7](https://china.xilinx.com/products/design-tools/ise-design-suite.html)
2. [Vivado 2018.3  (2020.2)](https://china.xilinx.com/products/design-tools/vivado/vivado-whats-new.html)

### 仿真软件
1. ModelSim : Mentor Graphics ModelSim SE 2020.4 x64 

### 综合工具
综合工具用于将HDL或者其它方式描述的设计电路转换成能够在可编程逻辑器件或者ASIC中实现的网表文件。是有软件设计转换成硬件实现的关键环节。

业界流行的FPG综合工具也有：

1. Synplify Pro
2. XST
3. Design Compiler II
4. RTL Compiler

---
## EDA技术的应用领域
EDA技术在通信工程，信息产业，半导体工业，消费类电子工业以及仪表工业等领域应用广泛。
1. 通信领域
2. 数字信号处理领域
3. 高速数据采集
4. 逻辑接口应用

5. 电平接口应用

## 电子系统的设计方法
1. 自顶向下
2. 自底向上
3. 上述两种方法的结合

---
## EDA网络学习资源汇总

学习EDA技术应该与时俱进，网络上会不断更新最新的学习资源，以及EDA技术在各种应用领域中的应用实例。
我们应该保持一颗持续接受新信息和新技术的心，始终保持好奇心。

所以，我在这里总结汇总网络上优秀的EDA学习资源。

[EDA技术学习资源汇总](1.1-EDA技术学习资源汇总.md)

---
