# STM32 学习笔记整理

ARM公司2007年首推出Cortex内核，ST凭借基于ARM CORTEX-M3内核的STM32F1，无疑成为了最大的赢家之一。特别是STM32F103系列，更是成为市场上最通用的MCU系列之一。
STM32F103器件采用Cortex-M3内核，CPU最高速度达72 MHz。该产品系列具有16KB ~ 1MB Flash、多种控制外设、USB全速接口和CAN。
ST在后续几年陆续推出了Cortex-M0+、Cortex-M4内核的芯片，并进行不断优化。

同类高性价比的芯片：

> ​       STM32F030----ARM Cortex-M0内核。最高主频48MHZ，特别是STM32F030F4，16K FLASH,4K RAM , TSSOP20封装。价格在3块钱左右。
> ​       STM32F042----同样Cortex-M0内核 。14年初推出的芯片，号称带USB，CAN总线的最便宜的MCU。可以和STM32F103系列 完全 PIN TO PIN 。适用于需要USB功能的小型电脑周边产品。
> ​       STM32L053----Cortex-M0+内核，14年推出。STM32L152系列的芯片我测过功耗，并没有我想象中的如意，比STM32F103略低，但比起市场上其他的低功耗MCU，并没有太明显的优势。但L053确实做得更好。主频32MHZ,最大FLASH 64kb.适用于低功耗要求苛刻的小型产品应用。跟STM32F103 PIN TO PIN
> ​       STM32F411--STM32系列中Cortex-M4内核中比较通用还是STM32F407系列，最高主频180MHZ。但这块STM32F401的特点在于其低功耗。运行功耗100uA/mhz,比32L053还略低。但由于是Cortex-M4内核，更方面功能会更强（最高主频84MHZ , FLASH 512kb）,十分适用于智能手环等可穿戴类产品。
> ​       STM32F303----各方面跟STM32F103一模一样，除了多了一个浮点运算，对于运算较多，很多Sensor数据处理的产品，可以考虑。

一张Flash memory size 图帮你快速选择芯片：

另外，ST的MCU系列种类繁多，光是芯片选型手册就有几十页。他们公司有一套命名规则，用来帮助使用者合理高效地进行芯片的选择。以下是ST公司的芯片产品命名规则截图：

最新：



## 一、 STM32F103学习路线图
我将在未来的三个月中，更新不带操作系统的知识的学习。

## 二、 目录
### [2.1 STM32时钟系统]()
### [2.2 STM32 GPIO笔记]()