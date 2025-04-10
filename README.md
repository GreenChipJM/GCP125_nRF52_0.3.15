# GCP125

# **GCP125**

- 可穿戴设备生物医学开发平台
    - 硬件 - 单通道GCP125 蓝牙主板 / 生物传感器板 （ECG、EMG、PPG、EEG）
    - 固件 - 使用 Arduino IDE 开发或恢复 GCP125蓝牙主板
    - 软件 - 适用于 GCP125 的 IOS、Android 应用程序

# **固件**

本文档包括以下内容：

1. **[对于用户]** 使用**出厂设置**轻松获取主板 和传感器板的数据。
2. [对于开发人员]您需要了解的有关 GCP125 作为微控制器的基本信息。
    
    **A. GCP125 描述**
    
    **B. 使用Arduino IDE 进行开发**
    
3. 常见问题 **（FAQ）**

# 1. [用户端] GCP125出厂设置和使用

- **A. GCP125有 1 个通道用于连接传感器板。**

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)

- **B. 快速启动步骤：**
    - 选择传感器板和软件
        - 传感器板：ECG、EEG、EMG、PPG
        - 软件 - 适用于 GCP125 的Android 应用程序
    - 在GCP125上组装传感器板。
    - 连接GCP125和APP，然后获得生物信号
- **C. 一个启动示例：**
    - 选择EEG子板作为传感器板，然后选择Android应用程序作为软件
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image2.png?raw=true)
    
    - 将传感器板插入GCP125母板，然后将电极线的3.5mm头插入传感板，电极人体太阳穴两端
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)
    
    - Android 应用程序：扫描、连接，然后转动眼球开始显示生物信号
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)
    
- **D. 其他不同情况的固件：**
    - 用于**无线**通信
        - 固件：
            - GCP125 Official Firmware：GCP125出厂固件
            - GCP125 ECG_BT：GCP125母板上LED会随心跳脉冲闪烁
            - GCP125 PPG_BT：GCP125母板上LED会随心跳脉冲闪烁
            - GCP125 EEG_BT：GCP125母板上LED会随眼睛左右看控制其亮灭
            - GCP125 EMG_BT：GCP125母板上LED会肌肉收缩点亮
        - 软件：安卓（BLE102）
- **E.如何将出厂设置固件更改为其他固件？**
    - **Arduino BSP 方法**
        - **a**. 将GCP125.rar放到C:\Users\admin\AppData\Local\Arduino15\packages目录下解压
        - **b**. 启动 Arduino IDE
        - **c**. 选择工具 > 开发板 > GCP125 Board（nRF52 Series）> GCP125 nRF52840
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image6.png?raw=true)
            
        - **d**. 选择工具 > 编程器 > GCP125 Official Firmware
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image7.png?raw=true)
            
        - **e**. 选择工具 > 端口 > COMXX (GCP125 nRF52840)
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image8.png?raw=true)
            
        - **f**. 选择工具 > 烧录引导程序
        - **g**. 等待大约 5~10 秒，如果跳出以下表扬，则表示**未成功**，请按照以下步骤操作。
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image9.png?raw=true)
            
        - **h**. 选择工具 > 端口 > COMYY (GCP125 nRF52840)**（YY 不会等于 XX）**
        - **i**. 选择工具 > 烧录引导程序
        - **j**. 等待大约 10~30 秒，如果显示以下表扬，则表示**成功**。
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image10.png?raw=true)
            

# **2. [对于开发人员] GCP125 出厂设置和使用**

**A. GCP125 描述**

- a. 引脚配置
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image11.png?raw=true)
    
- **b.Pin 功能描述**
位号	脚位	说明	位号	脚位	说明
1	P1.10	General-purpose I/O 
(standard drive, low frequency I/O only)	2	P1.11	General-purpose I/O 
(standard drive, low frequency I/O only)
3	P1.12	General-purpose I/O 
(standard drive, low frequency I/O only)	4	P1.13	General-purpose I/O 
(standard drive, low frequency I/O only)
5	P1.14	General-purpose I/O 
(standard drive, low frequency I/O only)	6	P1.15	General-purpose I/O 
(standard drive, low frequency I/O only)
7	P0.03/AIN1	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input	8	P0.29/AIN5	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input
9	P0.02/AIN0	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input	10	P0.31/AIN7	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input
11	P0.28/AIN4	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input	12	P0.30/AIN6	General-purpose I/O
 (standard drive, low frequency I/O only);
Analog input
13	P1.04	General-purpose I/O 
(standard drive, low frequency I/O only)	14	P1.06	General-purpose I/O 
(standard drive, low frequency I/O only)
15	P0.27	General-purpose I/O	16	P1.07	General-purpose I/O 
(standard drive, low frequency I/O only)
17	P0.26	General-purpose I/O	18	P0.04/AIN2	General-purpose I/O;
Analog input
19	P0.05/AIN3	General-purpose I/O;
Analog input	20	P0.06	General-purpose I/O
21	P0.07/TRACECLK	General-purpose I/O;
Trace buffer clock	22	P0.08	General-purpose I/O
23	P1.08	General-purpose I/O	24	GND	Ground
25	P0.10	General-purpose I/O	26	P0.09	General-purpose I/O
27	P1.02	General-purpose I/O 
(standard drive, low frequency I/O only)	28	P0.25	General-purpose I/O
29	P0.24	General-purpose I/O	30	P1.00/TRACEDATA0	General-purpose I/O;
Trace buffer TRACEDATA[0]
31	P0.22	General-purpose I/O;
(recommended usage: (QSPI)	32	P0.23	General-purpose I/O;
(recommended usage: (QSPI)
33	P0.20	General-purpose I/O	34	P0.21	General-purpose I/O;
(recommended usage: (QSPI)
35	P0.19	General-purpose I/O;
(recommended usage: (QSPI / SCK)	36	P0.17	General-purpose I/O
37	P0.18/nRESET	General-purpose I/O;
Configurable as system RESET	38	P0.15	General-purpose I/O
39	P0.16	General-purpose I/O	40	P0.13	General-purpose I/O
41	P0.14	General-purpose I/O	42	P1.01	General-purpose I/O 
(standard drive, low frequency I/O only)
43	P1.03	General-purpose I/O 
(standard drive, low frequency I/O only)	44	P1.05	General-purpose I/O 
(standard drive, low frequency I/O only)
45	P0.12/TRACEDATA1	General-purpose I/O;
Trace buffer TRACEDATA[1]	46	P0.11/TRACEDATA2	General-purpose I/O;
Trace buffer TRACEDATA[2]
47	P1.09/TRACEDATA3	General-purpose I/O;
Trace buffer TRACEDATA[3]	48	GND	Ground

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image12.png?raw=true)

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image13.png?raw=true)

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image14.png?raw=true)

![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image15.png?raw=true)

**B. 在 Arduino IDE 上使用 GCP125 进行开发**

- ***a. 环境建立***：将我司提供的GCP125.rar放到C:\Users\admin\AppData\Local\Arduino15\packages目录下解压
    - I. [下载并安装 Arduino IDE](https://www.arduino.cc/en/Main/Software)（最新版）
        - 选择操作系统的版本。
        - 直接按捐赠页面中的**“Just Download”。**
            
            ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image16.png?raw=true)
            
    - II. 将GCP125.rar放到C:\Users\admin\AppData\Local\Arduino15\packages目录下解压
    - III. 启动 Arduino IDE
    - IV. 选择 Boards Manager
        - 选择工具 > 开发板 > GCP125 Board（nRF52 Series）> GCP125 nRF52840
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image17.png?raw=true)
        
- **b. 上传并运行您的代码**
    - I. 选择一个示例代码或制作您自己的代码。文件 > 示例 > GCP125 > ECG_BT
    - II. 将 GCP125母板与 PC 连接。（建议：使用 USB 作为电源）
    - III. 选择工具 > 开发板 > GCP125 Board（nRF52 Series）> GCP125 nRF52840
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image18.png?raw=true)
        
    - IV. 选择工具 > 端口 > COMXX (GCP125 nRF52840)
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image19.png?raw=true)
        
    - V. 按 （编译 + 上传），或按 （编译），然后按 （上传））。
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image20.png?raw=true)
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image21.png?raw=true)
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image22.png?raw=true)
        
    - **上传成功 👋 显示 Device programmed （设备已编程）**
        
        ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image23.png?raw=true)
        

**附录。如果你遇到了什么麻烦......尝试重新烧录 Bootloader!!!**

方法 1：仅通过 USB 数据线将 GCP125-MDBT50Q板连接到 PC。

方法 2： 通过 J-Link 设备和 USB 数据线将GCP125-MDBT50Q板连接到 PC。（仅限致命错误）

- ------------------------------------------------------------**方法 1**
- I. 选择工具 > 开发板 > GCP125 Board（nRF52 Series）> GCP125 nRF52840
- II. 选择工具 > 端口 > COMXX (GCP125 nRF52840)
- III. 选择工具 > 编程器 > GCP125 Official Firmware
- IV. 选择工具 >烧录引导程序
- V. 等待约 20~30 秒。
- **成功刻录的图**
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image24.png?raw=true)
    

**方法 2**

- I. 要使用 J-Link，用户应在此处安装驱动程序[**。**](https://www.segger.com/downloads/jlink/)
- II. 选择您的操作系统并点击下载。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image25.png?raw=true)
    
- III. 安装驱动程序。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image26.png?raw=true)
    
- IV. 将 GCP125-MDBT50Q和 J-link 连接到您的 PC。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image27.png?raw=true)
    
- V. 启动 Arduino IDE。
- VI. 选择工具 > 端口 > COMZ（J-Link端口）
- VII. 选择工具 > 编程器 > J-Link for GCP125 nRF52
- VIII. 选择工具 >烧录引导程序
- IX. 等待约 20~30 秒。
- **成功刻录的图**
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image28.png?raw=true)
    

# **3. [常见问题 （FAQ）]**

**Q1 -> 如果您对** GCP125**默认固件有问题......**

1. 请确认你的 arduino IDE 在执行GCP125**默认固件 / 应用程序 - 固件设置步骤**中的步骤后，是否有下图所示的注释。
    
    ![](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image29.png?raw=true)
    
2. 请勿移除您的设备并重新执行GCP125 **默认固件/应用程序 - 固件设置步骤**的第 4~5 步。

**Q2 -> 如果您在 Arduino IDE 中工具 > 开发板无法找到GCP125**

1. 请下载最新的 Arduino IDE 版本。
