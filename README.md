# **GCP125**

- 可穿戴设备生物医学开发平台
    - **硬件**：单通道 GCP125 蓝牙主板及生物传感器板（支持 ECG、EMG、PPG、EEG）
    - **固件**：基于 Arduino IDE 开发的出厂固件与多种应用固件
    - 软件 - 适用于 GCP125 的Android 应用程序

# 目录

本文档包括以下内容：

1. **[用户指南]** 使用**出厂设置**轻松获取主板 和传感器板的数据。
2. [开发者指南] 您需要了解的有关 GCP125 的基本信息。
    
    **A. GCP125 描述**
    
    **B. 使用Arduino IDE 进行开发**
    
3. 常见问题 **（FAQ）**

# 1. [用户指南] GCP125出厂设置和使用

- **A. GCP125有 1 个通道用于连接传感器板。**

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)

- **B. 快速启动步骤：**
    - 选择传感器板和软件
        - 传感器板：ECG、EEG、EMG、PPG
        - 软件 - 适用于 GCP125 的Android 应用程序
    - 各传感器粘贴人体的方式
        1. ECG
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image2.png?raw=true)
        
        1. EEG
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image3.png?raw=true)
        
        1. EMG
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image4.png?raw=true)
        
        1. PPG
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image5.png?raw=true)
        
    - 在GCP125上组装传感器板。
    - 连接GCP125和APP，然后获得生物信号
- **C. 一个启动示例：**
    - 选择EEG子板作为传感器板，然后选择Android应用程序作为软件
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image6.png?raw=true)
    
    - 将传感器板插入GCP125母板，然后将电极线的3.5mm插头头插入传感板，电极线另一端安装两片电极贴，电极贴在人体太阳穴两端
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image7.png?raw=true)
    
    - Android 应用程序：打开APP并搜索、连接ALANO BLE，然后转动眼球开始显示生物信号
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image8.png?raw=true)
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image9.png?raw=true)
    
- **D. 其他不同情况的固件：**
    - 用于**无线**通信
        - 固件：
            - GCP125 Official Firmware：GCP125出厂固件
            - GCP125 ECG_BT：GCP125母板上LED会随心跳脉冲闪烁
            - GCP125 PPG_BT：GCP125母板上LED会随心跳脉冲闪烁
            - GCP125 EEG_BT：GCP125母板上LED会随眼睛左右看控制其亮灭
            - GCP125 EMG_BT：GCP125母板上LED会肌肉收缩点亮
- **E.如何将出厂设置固件更改为其他固件？**
    - **a**. 将GCP125蓝牙主板与PC通过USB转USB MINI连接线连接起来
    - b. [安装最新版Arduino IDE](https://www.arduino.cc/en/software/)
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image10.png?raw=true)
    
    - c. 启动Arduino ADE，点击File > Preferences，点击Additional boards manager URLs，将[https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json](https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json)填入并点击OK
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image11.png?raw=true)
    
    - d. 点击Tools > Board > Boards Manager
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image12.png?raw=true)
    
    - e. 在弹出的界面点击搜索栏输入GreenChip, 然后点击INSTALL
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image13.png?raw=true)
    
    - f. 选择Tools > Board > GreenChip GCP125 > GCP125 nRF52840
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image14.png?raw=true)
    
    - g. 选择Tools > Programmer > GCP125 ECG_BT
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image15.png?raw=true)
    
    - h. 选择Tools> Port > COMXX (GCP125 nRF52840)
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image16.png?raw=true)
    
    - i. 选择Tools > Burn Bootloader
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image17.png?raw=true)
    
    - j. 等待大约 5~10 秒，如果跳出以下表扬，则表示**未成功**，请按照以下步骤操作。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image18.png?raw=true)
    
    - k. 选择Tools > Port > COMYY (GCP125 nRF52840)**（YY 不会等于 XX）**
    - l. 选择Tools > Burn Bootloader
    - m. 等待大约 10~20 秒，如果显示以下表扬，则表示**成功**。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image19.png?raw=true)
    

# **2. [开发者指南] GCP125 固件开发**

**A. GCP125 描述**

- a. 引脚配置
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image20.png?raw=true)
    
    | 位号 | 脚位 | 说明 | 位号 | 脚位 | 说明 |
    | --- | --- | --- | --- | --- | --- |
    | 1 | P1.10 | General-purpose I/O | 2 | P1.11 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  | (standard drive, low frequency I/O only) |
    | 3 | P1.12 | General-purpose I/O | 4 | P1.13 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  | (standard drive, low frequency I/O only) |
    | 5 | P1.14 | General-purpose I/O | 6 | P1.15 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  | (standard drive, low frequency I/O only) |
    | 7 | P0.03/AIN1 | General-purpose I/O | 8 | P0.29/AIN5 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only); |  |  | (standard drive, low frequency I/O only); |
    |  |  | Analog input |  |  | Analog input |
    | 9 | P0.02/AIN0 | General-purpose I/O | 10 | P0.31/AIN7 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only); |  |  | (standard drive, low frequency I/O only); |
    |  |  | Analog input |  |  | Analog input |
    | 11 | P0.28/AIN4 | General-purpose I/O | 12 | P0.30/AIN6 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only); |  |  | (standard drive, low frequency I/O only); |
    |  |  | Analog input |  |  | Analog input |
    | 13 | P1.04 | General-purpose I/O | 14 | P1.06 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  | (standard drive, low frequency I/O only) |
    | 15 | P0.27 | General-purpose I/O | 16 | P1.07 | General-purpose I/O |
    |  |  |  |  |  | (standard drive, low frequency I/O only) |
    | 17 | P0.26 | General-purpose I/O | 18 | P0.04/AIN2 | General-purpose I/O; |
    |  |  |  |  |  | Analog input |
    | 19 | P0.05/AIN3 | General-purpose I/O; | 20 | P0.06 | General-purpose I/O |
    |  |  | Analog input |  |  |  |
    | 21 | P0.07/TRACECLK | General-purpose I/O; | 22 | P0.08 | General-purpose I/O |
    |  |  | Trace buffer clock |  |  |  |
    | 23 | P1.08 | General-purpose I/O | 24 | GND | Ground |
    | 25 | P0.10 | General-purpose I/O | 26 | P0.09 | General-purpose I/O |
    | 27 | P1.02 | General-purpose I/O | 28 | P0.25 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  |  |
    | 29 | P0.24 | General-purpose I/O | 30 | P1.00/TRACEDATA0 | General-purpose I/O; |
    |  |  |  |  |  | Trace buffer TRACEDATA[0] |
    | 31 | P0.22 | General-purpose I/O; | 32 | P0.23 | General-purpose I/O; |
    |  |  | (recommended usage: (QSPI) |  |  | (recommended usage: (QSPI) |
    | 33 | P0.20 | General-purpose I/O | 34 | P0.21 | General-purpose I/O; |
    |  |  |  |  |  | (recommended usage: (QSPI) |
    | 35 | P0.19 | General-purpose I/O; | 36 | P0.17 | General-purpose I/O |
    |  |  | (recommended usage: (QSPI / SCK) |  |  |  |
    | 37 | P0.18/nRESET | General-purpose I/O; | 38 | P0.15 | General-purpose I/O |
    |  |  | Configurable as system RESET |  |  |  |
    | 39 | P0.16 | General-purpose I/O | 40 | P0.13 | General-purpose I/O |
    | 41 | P0.14 | General-purpose I/O | 42 | P1.01 | General-purpose I/O |
    |  |  |  |  |  | (standard drive, low frequency I/O only) |
    | 43 | P1.03 | General-purpose I/O | 44 | P1.05 | General-purpose I/O |
    |  |  | (standard drive, low frequency I/O only) |  |  | (standard drive, low frequency I/O only) |
    | 45 | P0.12/TRACEDATA1 | General-purpose I/O; | 46 | P0.11/TRACEDATA2 | General-purpose I/O; |
    |  |  | Trace buffer TRACEDATA[1] |  |  | Trace buffer TRACEDATA[2] |
    | 47 | P1.09/TRACEDATA3 | General-purpose I/O; | 48 | GND | Ground |
    |  |  | Trace buffer TRACEDATA[3] |  |  |  |

**B. 在 Arduino IDE 上使用 GCP125 进行开发**

- **a**. 将GCP125蓝牙主板与PC通过USB转USB MINI连接线连接起来
- b. [安装最新版Arduino ADE](https://www.arduino.cc/en/software/)

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image10.png?raw=true)

- c. 启动Arduino ADE，点击File > Preferences，点击Additional boards manager URLs，将[https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json](https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json)填入并点击OK

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image11.png?raw=true)

- d. 点击Tools > Board > Boards Manager

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image12.png?raw=true)

- e. 在弹出的界面点击搜索栏输入GreenChip, 然后点击INSTALL

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image13.png?raw=true)

- f. 选择FIle > Examples > GCP125 > ECG_BT或其他示例

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image21.png?raw=true)

- g. 选择Tools > Board > GreenChip GCP125 > GCP125 nRF52840

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image14.png?raw=true)

- h. 选择Tools> Port > COMXX (GCP125 nRF52840)

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image16.png?raw=true)

- i. 按下编译+上传按键, 等待烧录, 烧录成功显示Device programmed

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image22.png?raw=true)

**C. 附录。如果你遇到了什么麻烦......尝试重新烧录 Bootloader!!!**

方法 1：仅通过 USB 数据线将 GCP125蓝牙主板板连接到 PC。

- I. 选择Tools > Board > GreenChip GCP125> GCP125 nRF52840
- II. 选择Tools > Port > COMXX (GCP125 nRF52840)
- III. 选择Tools > Programmer > GCP125 Official Firmware
- IV. 选择Tools > Burn Bootloader
- V. 等待约 10~20 秒。
- **成功刻录的图**

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image23.png?raw=true)

方法 2： 通过 J-Link 设备和 USB 数据线将GCP125蓝牙主板连接到 PC。（仅限致命错误）

- I. 要使用 J-Link，用户应在此处安装驱动程序[**。**](https://www.segger.com/downloads/jlink/)
- II. 选择您的操作系统并点击下载。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image24.png?raw=true)
    
- III. 安装驱动程序。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image25.png?raw=true)
    
- IV. 将 GCP125-MDBT50Q和 J-link 连接到您的 PC。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image26.png?raw=true)
    
- V. 启动 Arduino IDE。
- VI. 选择Tools > Board > GreenChip GCP125> GCP125 nRF52840
- VII. 选择Tools > Port > COMXX (GCP125 nRF52840)
- VIII. 选择Tools > Programmer > J-Link for GCP125 nRF52
- IX. 选择Tools > Burn Bootloader
- X. 等待约 10~20 秒。
- **成功刻录的图**
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image27.png?raw=true)
    

# **3. [常见问题 （FAQ）]**

**Q1 -> 如果您对** GCP125**默认固件有问题......**

1. 请确认你的 arduino IDE 在执行GCP125**默认固件 / 应用程序 - 固件设置步骤**中的步骤后，是否有下图所示的注释。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image28.png?raw=true)
    
2. 请勿移除您的设备并重新执行GCP125 **默认固件/应用程序 - 固件设置步骤**的第 4~5 步。

**Q2 -> 如果您在 Arduino IDE 中工具 > 开发板无法找到GCP125**

请下载最新的 Arduino IDE 版本。
