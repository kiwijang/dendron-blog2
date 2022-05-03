
## 電腦系統概論 computer system structure

### 組成電腦的五大單元

![](/assets/images/2022-05-02-22-40-17.png)

> 圖源: [第零章、計算機概論 - 鳥哥](https://linux.vbird.org/linux_basic/centos7/0105computers.php#ps4)

![](/assets/images/2022-05-02-22-46-40.png)

> 圖源: [馮紐曼架構 Von Neumann architecture](https://zh-yue.wikipedia.org/wiki/%E9%A6%AE%E7%B4%90%E6%9B%BC%E6%9E%B6%E6%A7%8B)/[Computer Organisation](https://en.wikibooks.org/wiki/IB/Group_4/Computer_Science/Computer_Organisation)

1. 輸入單元 input device
2. 輸出單元 output device
3. CPU 內部的控制單元 control unit
4. CPU 內部的算數邏輯單元 arithmetic/logic unit (ALU)
5. 主記憶體 memory unit

### 電腦系統粗分為四元件

![](/assets/images/2022-05-02-23-43-42.png)

1. 硬體 hardware

   例如: cpu、disk、memory...

2. 作業系統 operating system

3. 應用程式與系統程式 application programs and sys programs

4. 使用者 users

   例如: 人、其他機器、其他系統...

## 作業系統概述 OS Structure

### OS 的目的

### 電腦系統架構

1. 多處理器系統 Multiprocessor System / Parallel System / Tightly Coupled System

   1. 最常見為 SMP(Symmetric Multi-Processing)

      對稱式多處理器記憶體資源是共享的又稱 UMA(Uniform Memory Access)，所以會有資源競爭的問題。可用 CPU 排程和同步工具來解決遇到的問題(CH5、CH6)。

      雙核(dual-core)設計的處理器將多個 CPU 放置同一晶片(chips)上，會比個放在不同晶片上更有效率且更省電(省電對筆電和手機來說很重要)。

      快取級數越小代表體積越小、速度越快。

      這種共用資源的 CPU 架構讓 OS 設計及程式設計變得很重要(CH4 執行緒與並行)。

      ![](/assets/images/2022-05-03-22-41-34.png)

      > 圖源: [Cache Memory | L1, L2 and L3 Caches in Computers | L1 L2 L3 Cache Explained in Hindi](https://www.youtube.com/watch?v=IU9cB5g4eZU&ab_channel=ITSimplifiedinHINDI)

      當 CPU 變多，處理器和記憶體間的匯流排將會成為資料存取的瓶頸，會嚴重地影響到系統效能。[註 1]

      為了解決多 CPU 的資源競爭問題，NUMA (Non-Uniform Memory Access) 的設計簡化了匯流排的複雜程度，NUMA 將處理器切成不同節點，每個處理器都有各自的連結，當要用到別的節點的記憶體時速度會變慢，但只用到自己的記憶體時不只速度快、也不會有資源競爭的問題(因為自己用自己的，去用別人的也只會有一條路)。

      1. ![](/assets/images/2022-05-03-23-52-25.png)

      2. > 圖源: [A NUMA architecture with 4 nodes - uploaded by Li Wang](https://www.researchgate.net/figure/A-NUMA-architecture-with-4-nodes_fig2_273393420)

   1. ASMP(Asymmetric MultiProcessors) 非對稱式多處理器:通常採主從式架構。比 SMP 效能還差，主 CPU 易有效能瓶頸，且可靠度也差(主 CPU 壞了就全不能用)。

   1. 叢集式系統 clustered system

      1. 也是一種多處理器系統(Multiprocessor System)

2. 分散式系統 Distributed System / Loosely Coupled system

   多部機器彼此以網路相互串聯。機器間硬體資源不共享、各 CPU 時脈(clock)控制不一定相同、各 CPU 上的 OS 也不一定相同、處理器之間的溝通大都採 Message Passing 方式 (CH6)。

   增加吞吐量(throughput)和可靠性(reliability)、減少資源共享、可滿足遠端通訊的需求。

   可分成主從式架構與 P2P 架構。(就像 ASMP 和 NUMA 概念的差別，不是主從就是平權欸...)

### 作業系統執行

2. 多元程式設計系統 Multiprogramming

   1. 分時系統 Time-Sharing / Multitasking

3. Dual-Mode and Multimode Operation

4. Timer

5. 批次系統 Batch System

---

6. 即時系統 Real-Time System

   1. Hard
   2. Soft

7. 手持系統 handheld system

## 參考資料

- 註一 [多核心計算環境—NUMA 與 CPUSET 簡介 by 周秉誼](https://www.cc.ntu.edu.tw/chinese/epaper/0015/20101220_1508.htm)

#### 名詞解釋

- CPU

  執行指令(instructions)的硬體。

- 處理器 Processor

  包含一或多個 CPU 的物理晶片(chip)。

- 核心 Core

  CPU 的基本數量單位。

- 多核心 Multicore

  同 CPU 上包含多個運算核心。

- Multiprocessor

  包含多個處理器。
