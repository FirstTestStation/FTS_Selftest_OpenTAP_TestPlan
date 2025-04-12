
# OpenTAP Selftest Test Plan 800-1010-xx


This repository contains the OpenTAP Test Plan sequences to be used to perform the **Selftest** of the First TestStation (FTS) project. <br>

OpenTAP Test Plan are available to run the sequence with or without external instruments, and with or without external loopback connectors.



## Sequence

This section lists the OpenTAP Test Plan available in the repository. <br>

The selftest sequence is built upon guidelines from the [SelfTest Strategies Document](https://github.com/FirstTestStation/FirstTestStation/tree/main/pdf/Selftest_Strategy.pdf).<br>

The sequence adheres to the instructions outlined in the table [Validation_Test_200-1000.pdf](https://github.com/FirstTestStation/FirstTestStation/tree/main/pdf/Validation_Test_200-1000.pdf)

### Available Sequences

- **Selftest_800-1010.TapPlan**  
  Complete selftest Test Plan sequence, utilizing a loopback connector but no external instruments.

- **Selftest_Loopback.TapPlan**  
  Selftest Test Plan to verify the functionality of the loopback connector.

- **Selftest_noLoopback.TapPlan**  
  Selftest Test Plan without the external loopback connector.


## OpenTAP

[OpenTAP](https://opentap.io/) is an open-source test sequencer designed for hardware and software test automation. 

However, the version available for download from the official site requires manual typed commands to install packages and lacks an integrated editor, making it less user-friendly for some users.

**Keysight** has developed a more comprehensive package based on OpenTAP. This package includes everything needed to install additional applications and run OpenTAP sequences seamlessly.


## Prerequisites
- [Keysight OpenTAP Test Automation](https://www.keysight.com/ca/en/lib/software-detail/computer-software/pathwave-test-automation-2796935.html). OpenTAP complete package
- [First TestStation InterconnectIOBox OpenTAP Plugin](https://github.com/FirstTestStation/FTS_InterconnectIOBox_OpenTAP_Plugin) The OpenTAP plugin to control the InterconnectIO Box
- [Keysight IO Libraries Suite](https://www.keysight.com/ca/en/lib/software-detail/computer-software/keysight-instrument-control-bundle-download-1184883.html) (2023 or higher). Communication with the InterconnectIOBox uses the RS-232 protocol exclusively. However, additional external instruments may use different protocols.<br> The free Keysight Instrument Control Bundle is designed to support a variety of instrument types and communication standards.


### Graphical User Interface

OpenTAP requires a graphical user interface to load and run test sequences. Several GUIs are available for OpenTAP, some free and others requiring licenses:

- **TUI**  
  The *Text-Based User Interface (TUI)* is completely free and has been validated with the self-test sequence.

- **Keysight GUIs**  
  Keysight offers two GUIs: **Editor** and **EditorX**. Both are available under a free **Community License** or as an **Enterprise Edition**.  
  - However, to enable the Community License, only **EditorX** supports license activation through a web-based login interface.

For this project, the **OpenTAP Editor** with a Community License was used to develop and run the sequence.

- **EditorX Link**

    [Keysight Editor X](https://www.keysight.com/ca/en/lib/software-detail/computer-software/pathwave-test-automation-2796935.html/) OpenTAP EditorX is available under a free Community License or as an Enterprise Edition.
<br>
<br>



# Installation and Setup Guide

## Steps

### 1. **Install Keysight IO Library Suite**  
   *Command Expert and BenchVue are optional.*

### 2. **Configure Keysight Connection Expert**  
   - Launch **Keysight Connection Expert**.
   - Add the COM instrument: `RS-232 115200,N81`.
   - Using **Interactive IO**, send and read the command `IDN?` to test communication with the *InterconnectIO Box*.

### 3. **Get OpenTAP Github repositories**
   - if Github not installed, [Github Desktop](https://desktop.github.com/download/)
   - Using Github Desktop, Clone the repositories:<br>
         https://github.com/FirstTestStation/FTS_Selftest_OpenTAP_TestPlan.git<br>
         https://github.com/FirstTestStation/FTS_InterconnectIOBox_OpenTAP_Plugin.git<br>


### 4. **Install OpenTAP Package**
   - Open **File Explorer** and navigate to the OpenTAP directory:  
     ```plaintext
     C:\Program Files\OpenTAP  or C:\Program Files\Keysight\Test Automation
     ```
   - Open **PackageManager.exe**.
   - In **Keysight Package Manager**, click **"+"** to open *File Explorer*.
   - from the plugin repositorie, select the latest **TapPackage** for *FTS_InterconnectIOBox*.
   - Wait until the installation is complete, then close *Package Manager*.


### 5. **Launch OpenTAP Editor**

   1. Navigate to the *OpenTAP* folder and open **Editor.exe**.
   2. In the lower-left corner:
      - Click on **DUTs**.
      - Press **+** to add a DUT module.
      - For the **DUT Module** line, click **Add**.
      - In the **FTS_DUT** window, select the 1-wire devices present on **J1** and **J2**.
   3. In the lower-middle corner:
      - Click on **Instruments**.
      - Press **+** to add an instrument.
      - For the **InterconnectIO** line, click **Add**.
      - In the **InterconnectIO** window, specify the VISA address to be used for communication (e.g., `ASRL1::INSTR`).
   4. In the Editor window:
      - Click **File** and load the desired sequences from the repository.
   5. To execute the test plan:
      - Press **F5** or click the green arrow.
      - Upon completion, the test plan will return a result: **PASS** or **FAIL**.


### 6. **Configure OpenTAP Editor**
   - In the *OpenTAP* folder, open **Editor.exe**.
   - On Left Bottom Corner, click on DUTs, click on "+", On **DUT Module** line click on button **Add**. On **FTS_DUT** window, click on 1-wire device present on J1 and 1-wire device present on J2.
   - On middle Bottom Corner, click on Instruments, click on "+", On **InterconectIO** line, click on button **Add**. On **InterconnectIO** window, select VISA Address to be used to communicate (example: ASRL1::INSTR)
  

### 7. **Execute the SelfTest Sequence**
   - On Editor window, click on File and load the desired Test Plan sequence from the repository.
   - press **F5** or click on green arrow to run the test plan,
   - Test Plan will execute and give final results PASS or FAIL when completed.



   


## Community License Requirement
If **OpenTAP Editor** requests a valid **Community License** to run OpenTAP sequences:
   - Launch **Editor X**. default location: C:\Program Files\Keysight\Test Automation Editor X\Packages\Editor X\application\Editor X.exe
   - Follow the instructions to login and enable the **Community License**.
   - After enabling the license, close the Editor X, the standard **OpenTAP Editor** include in Test Automation Bundle will function normally.

## Notes
- Ensure your system meets the necessary requirements.
- If encountering issues, check the documentation or seek support.

---



## License

These openTAP Test Plan (.TapPlan) is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
