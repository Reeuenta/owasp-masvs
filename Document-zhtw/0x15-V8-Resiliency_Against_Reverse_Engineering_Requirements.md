# V8: Resilience Requirements

# 控制目標

本節涵蓋對於存取機敏資料的功能的行動應用程序建議的縱身防禦措施。
缺少任何這些控件不會導致漏洞 - 相反的，它們打算增加逆向工程及特定的客戶端攻擊對行動應用程式的彈性


基於對未經授權篡改應用程式和/或代碼逆向工程所導致的風險的評估，應根據需要應用本節中的控件。
我們建議諮詢OWASP文件"逆向工程技術風險和未經授權的代碼修改逆向工程和代碼修改預防"(參考下面)列出的業務風險以及相關的技術威脅。

對下面的列表中的任何控件是有效的，應用程式必須滿足至少所有的MASVS-L1(換句話說，實體安全控件一定是到位)，以及V8內所有低編號的要求，
例如，下面的混淆控制列表"妨礙理解"一定是跟"應用程式隔離"結合，"妨礙動態分析和竄改"，和"設備綁定"

注意: 軟體保護絕不是使用在一個安全控制元件替換，MASVR-R中列出的控件旨在增加特定威脅，對滿足MASVS安全要求的應用程式，提供額外的保護控制

以下注意事項採用:

1. A threat model must be defined that clearly outlines the client-side threats defended against. Additionally, the grade of protection the scheme is meant to provide must be specified. For example, a stated goal could be to force authors of targeted malware seeking to instrument the app to invest significant manual reverse engineering effort.

2. The threat model must be sensical. For example, hiding a cryptographic key in a white-box implementation is besides the point if the attacker can simply code-lift the white-box as a whole. 

3. The effectiveness of the protection should always be verified by a human expert with experience in testing the particular types of anti-tampering and obfuscation used (see also the "reverse engineering" and "assessing software protections" chapters in the Mobile Security Testing Guide).

### 阻礙動態分析和篡改

| # | Description | R |
| --- | --- | --- |
| **8.1** | The app detects, and responds to, the presence of a rooted or jailbroken device either by alerting the user or terminating the app. | ✓ |
| **8.2** | The app prevents debugging and/or detects, and responds to, a debugger being attached. All available debugging protocols must be covered. | ✓ |
| **8.3** | The app detects, and responds to, tampering with executable files and critical data within its own sandbox. | ✓ |
| **8.4** | The app detects, and responds to, the presence of widely used reverse engineering tools and frameworks on the device.| ✓ |
| **8.5** | The app detects, and responds to, being run in an emulator.  | ✓ |
| **8.6** | The app detects, and responds to, tampering the code and data in its own memory space. | ✓ |
| **8.7** | The app implements multiple mechanisms in each defense category (8.1 to 8.6). Note that resiliency scales with the amount, diversity of the originality of the mechanisms used. | ✓ |
| **8.8** | The detection mechanisms trigger responses of different types, including delayed and stealthy responses. | ✓ |
| **8.9** | Obfuscation is applied to programmatic defenses, which in turn impede de-obfuscation via dynamic analysis.  | ✓ |

### Device Binding

| # | Description | R |
| --- | --- | --- |
| **8.10** | The app implements a 'device binding' functionality using a device fingerprint derived from multiple properties unique to the device. | ✓ |

### Impede Comprehension

| # | Description | R |
| --- | --- | --- |
| **8.11** |All executable files and libraries belonging to the app are either encrypted on the file level and/or important code and data segments inside the executables are encrypted or packed. Trivial static analysis does not reveal important code or data. | ✓ |
| **8.12** | If the goal of obfuscation is to protect sensitive computations, an obfuscation scheme is used that is both appropriate for the particular task and robust against manual and automated de-obfuscation methods, considering currently published research. The effectiveness of the obfuscation scheme must be verified through manual testing. Note that hardware-based isolation features are preferred over obfuscation whenever possible. | ✓ |

## References

The OWASP Mobile Security Testing Guide provides detailed instructions for verifying the requirements listed in this section.

- Android - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05j-Testing-Resiliency-Against-Reverse-Engineering.md
- iOS - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x06j-Testing-Resiliency-Against-Reverse-Engineering.md

For more information, see also:

- OWASP Mobile Top 10: M8 - Code Tampering, M9 - Reverse Engineering
- WASP Reverse Engineering Threats -https://www.owasp.org/index.php/Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification
- OWASP Reverse Engineering and Code Modification Prevention - https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project
