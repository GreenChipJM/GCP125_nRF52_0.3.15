# **GCP125**

- Wearable Biomedical Development Platform
  - **Hardware**: Single-channel GCP125 Bluetooth mainboard and biosensor board (supports ECG, EMG, PPG, EEG)
  - **Firmware**: Factory firmware developed based on Arduino IDE, along with various application firmware
  - **Software**: Android application for GCP125

# Table of Contents

This document includes the following content:

1. **[User Guide]** Easily obtain data from the mainboard and sensor board using **factory settings**.
2. **[Developer Guide]** Essential information you need to know about GCP125.
   - **A. GCP125 Description**
   - **B. Development with Arduino IDE**
3. **Frequently Asked Questions (FAQ)**

# 1. [User Guide] GCP125 Factory Settings and Usage

- **A. GCP125 has 1 channel for connecting the sensor board.**

![Sensor Board](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image1.png?raw=true)

- **B. Quick Start Steps:**
  - Select the sensor board and software
    - Sensor Boards: ECG, EEG, EMG, PPG
    - Software: Android application for GCP125
  - Placement of sensors on the body
    1. ECG
    
    ![ECG Placement](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image2.png?raw=true)
    
    2. EEG
    
    ![EEG Placement](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image3.png?raw=true)
    
    3. EMG
    
    ![EMG Placement](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image4.png?raw=true)
    
    4. PPG
    
    ![PPG Placement](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image5.png?raw=true)
    
  - Assemble the sensor board onto the GCP125.
  - Connect GCP125 to the app and obtain biosignals.
- **C. A Startup Example:**
  - Select the EEG sub-board as the sensor board and the Android application as the software.
  
  ![EEG Setup](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image6.png?raw=true)
  
  - Insert the sensor board into the GCP125 mainboard, plug the 3.5mm electrode cable into the sensor board, and attach two electrode patches to the other end of the cable. Place the electrode patches on both temples of the human body.
  
  ![Electrode Connection](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image7.png?raw=true)
  
  - Android Application: Open the app, search for and connect to ALANO BLE, then move your eyes to start displaying biosignals.
  
  ![App Connection](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image8.png?raw=true)
  
  ![Biosignal Display](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image9.png?raw=true)
  
- **D. Firmware for Other Scenarios:**
  - For **wireless** communication
    - Firmware:
      - GCP125 Official Firmware: Factory firmware for GCP125
      - GCP125 ECG_BT: LED on the GCP125 mainboard blinks with heart pulses
      - GCP125 PPG_BT: LED on the GCP125 mainboard blinks with heart pulses
      - GCP125 EEG_BT: LED on the GCP125 mainboard turns on/off based on left/right eye movement
      - GCP125 EMG_BT: LED on the GCP125 mainboard lights up with muscle contraction
- **E. How to Change Factory Firmware to Other Firmware?**
  - **a.** Connect the GCP125 Bluetooth mainboard to a PC using a USB-to-USB Mini cable.
  - **b.** [Install the latest version of Arduino IDE](https://www.arduino.cc/en/software/)
  
  ![Arduino IDE Installation](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image10.png?raw=true)
  
  - **c.** Launch Arduino IDE, click *File > Preferences*, click *Additional Boards Manager URLs*, enter [https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json](https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json), and click *OK*.
  
  ![Preferences](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image11.png?raw=true)
  
  - **d.** Click *Tools > Board > Boards Manager*.
  
  ![Boards Manager](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image12.png?raw=true)
  
  - **e.** In the pop-up window, type *GreenChip* in the search bar and click *INSTALL*.
  
  ![Install GreenChip](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image13.png?raw=true)
  
  - **f.** Select *Tools > Board > GreenChip GCP125 > GCP125 nRF52840*.
  
  ![Select Board](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image14.png?raw=true)
  
  - **g.** Select *Tools > Programmer > GCP125 ECG_BT*.
  
  ![Select Programmer](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image15.png?raw=true)
  
  - **h.** Select *Tools > Port > COMXX (GCP125 nRF52840)*.
  
  ![Select Port](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image16.png?raw=true)
  
  - **i.** Select *Tools > Burn Bootloader*.
  
  ![Burn Bootloader](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image17.png?raw=true)
  
  - **j.** Wait for approximately 5–10 seconds. If the following message appears, it indicates **failure**. Follow the steps below.
  
  ![Failure Message](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image18.png?raw=true)
  
  - **k.** Select *Tools > Port > COMYY (GCP125 nRF52840)* (**YY will not equal XX**).
  - **l.** Select *Tools > Burn Bootloader*.
  - **m.** Wait for approximately 10–20 seconds. If the following message appears, it indicates **success**.
  
  ![Success Message](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image19.png?raw=true)

# **2. [Developer Guide] GCP125 Firmware Development**

**A. GCP125 Description**

- **a. Pin Configuration**
  
  ![Pinout](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image20.png?raw=true)
  
  | Pin No. | Pin | Description | Pin No. | Pin | Description |
  |---------|-------|-------------|---------|-------|-------------|
  | 1 | P1.10 | General-purpose I/O | 2 | P1.11 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   | (standard drive, low frequency I/O only) |
  | 3 | P1.12 | General-purpose I/O | 4 | P1.13 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   | (standard drive, low frequency I/O only) |
  | 5 | P1.14 | General-purpose I/O | 6 | P1.15 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   | (standard drive, low frequency I/O only) |
  | 7 | P0.03/AIN1 | General-purpose I/O | 8 | P0.29/AIN5 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only); Analog input |   |   | (standard drive, low frequency I/O only); Analog input |
  | 9 | P0.02/AIN0 | General-purpose I/O | 10 | P0.31/AIN7 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only); Analog input |   |   | (standard drive, low frequency I/O only); Analog input |
  | 11 | P0.28/AIN4 | General-purpose I/O | 12 | P0.30/AIN6 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only); Analog input |   |   | (standard drive, low frequency I/O only); Analog input |
  | 13 | P1.04 | General-purpose I/O | 14 | P1.06 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   | (standard drive, low frequency I/O only) |
  | 15 | P0.27 | General-purpose I/O | 16 | P1.07 | General-purpose I/O |
  |   |   |   |   |   | (standard drive, low frequency I/O only) |
  | 聚焦 | P0.26 | General-purpose I/O | 18 | P0.04/AIN2 | General-purpose I/O; Analog input |
  | 19 | P0.05/AIN3 | General-purpose I/O; Analog input | 20 | P0.06 | General-purpose I/O |
  | 21 | P0.07/TRACECLK | General-purpose I/O; Trace buffer clock | 22 | P0.08 | General-purpose I/O |
  | 23 | P1.08 | General-purpose I/O | 24 | GND | Ground |
  | 25 | P0.10 | General-purpose I/O | 26 | P0.09 | General-purpose I/O |
  | 27 | P1.02 | General-purpose I/O | 28 | P0.25 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   |   |
  | 29 | P0.24 | General-purpose I/O | 30 | P1.00/TRACEDATA0 | General-purpose I/O; Trace buffer TRACEDATA[0] |
  | 31 | P0.22 | General-purpose I/O; (recommended usage: QSPI) | 32 | P0.23 | General-purpose I/O; (recommended usage: QSPI) |
  | 33 | P0.20 | General-purpose I/O | 34 | P0.21 | General-purpose I/O; (recommended usage: QSPI) |
  | 35 | P0.19 | General-purpose I/O; (recommended usage: QSPI / SCK) | 36 | P0.17 | General-purpose I/O |
  | 37 | P0.18/nRESET | General-purpose I/O; Configurable as system RESET | 38 | P0.15 | General-purpose I/O |
  | 39 | P0.16 | General-purpose I/O | 40 | P0.13 | General-purpose I/O |
  | 41 | P0.14 | General-purpose I/O | 42 | P1.01 | General-purpose I/O |
  |   |   |   |   |   | (standard drive, low frequency I/O only) |
  | 43 | P1.03 | General-purpose I/O | 44 | P1.05 | General-purpose I/O |
  |   |   | (standard drive, low frequency I/O only) |   |   | (standard drive, low frequency I/O only) |
  | 45 | P0.12/TRACEDATA1 | General-purpose I/O; Trace buffer TRACEDATA[1] | 46 | P0.11/TRACEDATA2 | General-purpose I/O; Trace buffer TRACEDATA[2] |
  | 47 | P1.09/TRACEDATA3 | General-purpose I/O; Trace buffer TRACEDATA[3] | 48 | GND | Ground |

**B. Developing with GCP125 on Arduino IDE**

- **a.** Connect the GCP125 Bluetooth mainboard to a PC using a USB-to-USB Mini cable.
- **b.** [Install the latest version of Arduino IDE](https://www.arduino.cc/en/software/).

![Arduino IDE Installation](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image10.png?raw=true)

- **c.** Launch Arduino IDE, click *File > Preferences*, click *Additional Boards Manager URLs*, enter [https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json](https://raw.githubusercontent.com/GreenChipJM/GCP125_Assets/refs/heads/main/package_GreenChip_index.json), and click *OK*.

![Preferences](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image11.png?raw=true)

- **d.** Click *Tools > Board > Boards Manager*.

![Boards Manager](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image12.png?raw=true)

- **e.** In the pop-up window, type *GreenChip* in the search bar and click *INSTALL*.

![Install GreenChip](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image13.png?raw=true)

- **f.** Select *File > Examples > GCP125 > ECG_BT* or other examples.

![Select Example](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image21.png?raw=true)

- **g.** Select *Tools > Board > GreenChip GCP125 > GCP125 nRF52840*.

![Select Board](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image14.png?raw=true)

- **h.** Select *Tools > Port > COMXX (GCP125 nRF52840)*.

![Select Port](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image16.png?raw=true)

- **i.** Press the *Compile + Upload* button, wait for the upload, and a successful upload will display *Device programmed*.

![Successful Upload](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image22.png?raw=true)

**C. Appendix: If You Encounter Issues... Try Re-burning the Bootloader!!!**

**Method 1**: Connect the GCP125 Bluetooth mainboard to a PC using only a USB cable.

- **I.** Select *Tools > Board > GreenChip GCP125 > GCP125 nRF52840*.
- **II.** Select *Tools > Port > COMXX (GCP125 nRF52840)*.
- **III.** Select *Tools > Programmer > GCP125 Official Firmware*.
- **IV.** Select *Tools > Burn Bootloader*.
- **V.** Wait for approximately 10–20 seconds.
- **Successful Burn Image**

![Successful Burn](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image23.png?raw=true)

**Method 2**: Connect the GCP125 Bluetooth mainboard to a PC using a J-Link device and USB cable (for critical errors only).

- **I.** To use J-Link, install the drivers [here](https://www.segger.com/downloads/jlink/).
- **II.** Select your operating system and click download.

![J-Link Download](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image24.png?raw=true)

- **III.** Install the drivers.

![Driver Installation](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image25.png?raw=true)

- **IV.** Connect the GCP125-MDBT50Q and J-Link to your PC.

![J-Link Connection](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image26.png?raw=true)

- **V.** Launch Arduino IDE.
- **VI.** Select *Tools > Board > GreenChip GCP125 > GCP125 nRF52840*.
- **VII.** Select *Tools > Port > COMXX (GCP125 nRF52840)*.
- **VIII.** Select *Tools > Programmer > J-Link for GCP125 nRF52*.
- **IX.** Select *Tools > Burn Bootloader*.
- **X.** Wait for approximately 10–20 seconds.
- **Successful Burn Image**

![Successful J-Link Burn](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image27.png?raw=true)

# **3. [Frequently Asked Questions (FAQ)]**

**Q1 -> If you have issues with the default GCP125 firmware...**

1. Confirm whether your Arduino IDE displays the annotation shown below after completing the steps in **Default Firmware/Application - Firmware Setup Steps**.

![Firmware Issue](https://github.com/GreenChipJM/GCP125_Assets/blob/main/png/image28.png?raw=true)

2. Do not remove your device and re-execute steps 4–5 of the **Default Firmware/Application - Firmware Setup Steps**.

**Q2 -> If you cannot find GCP125 under Tools > Board in Arduino IDE**

Please download the latest version of Arduino IDE.
