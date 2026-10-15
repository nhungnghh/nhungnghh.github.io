---
layout: post
title: "Part 5: Dynamic Analysis"
date: 2026-10-06
description: "Part 5: Dynamic Analysis"
---
# Dynamic Analysis
## Defines
- Dynamic analysis refers to the examination of software or computer programs while they are running.
- It aims to directly observe and understand the program's behavior, detecting potential bugs, security vulnerabilities, performance issues, or malicious functions.
## Dynamic analysis used for
- **Real-Time Analysis**: Dynamic analysis test how a program responds to various inputs in real-time, allowing for the identification of runtime errors and behaviors not visible during static analysis(hành vi không thể nhìn thấy trong quá trình phân tích tĩnh).
- **Malware Detection**: Dynamic analysis can identify malicious activities by observing how malware behaves, which system resources it tries to access, the network connections it uses, and which files it attempts to modify.
- **Performance Evaluation**: It asseses application performance through metrics like memory usage, CPU load, and response times, which is critical for optimizing applications.
- **Integration Testing**: It checks how software interacts with other systems and APIs, identifying integration errors and incompatibilities.
Dynamic analysis is performed using various tools, including debuggers(like GDB, OllyDbg), system monitoring tools (Process Monitor), and network analysis tools (Wireshark). Additionally, automated sandbox systems provide isolation and analysis, particularly for malware.
Malware often employs various techniques to avoid detection during dynamic analysis. Some of these techniques are as follows:
- **Debugger detectiion**: malware attempts to identify the presence of a debugger on the system its operates. If a debugger is active, the malware may terminate its malicious act or hide its harmful behaviors.
- **Virtual Machine Detection**: malware checks whether it runs in a virtual machine env by collecting hardware infor about its OS. For instance, if it detect 1GB of RAM and a single-core CPU, it may conclude that it runs in a VM and within a sandbox env. If it identifies that it is in a VM, it may stop execution or conceal (che giấu) its malicious act.
- **Time Delay Tactics**: Some malware may go into (đi vào) a wait state or delay certain actions for a specified period to complicate the analysis process.
- **Obfuscation and Polymorphism**: Malware can complicate analysis by obfuscating its code or frequently changing it (polymorphism).
- **Anti-Debugging Techniques**: these techniques make it difficult for debuggers to monitor the malware. For example, malware may monitor changes in the OS to determine the presence of a debugger.
- **Variable Analysis**: Particularly targeted malware analyzes the system to validate its target. For instance, it may detect the system's internet IP address to ascertain (xác định) its location, check the system clock for time zone information, verify if the system is part of a domain structure, and assess (đánh giá) CPU and RAM amounts, among other methods.

## Dynamic Analysis Tools
- SysInternals Tools comprise (bao gồm) a software suite developed by Microsoft that includes various powerful monitoring, management, and information-gathering tools for Windows OS.
### Process Monitor (ProcMon.exe)
- ProcMon monitors system events such as **file system, registry and network activity in Windows OS in real time and records** them in detail.
  - **File System Activity**: Các thao tác với file và thư mục như tạo, đọc, ghi, xóa hoặc truy cập file
  - **Registry**: Các thao tác với Windows Registry như tạo, đọc, chỉnh sửa hoặc xóa Registry key/value
  - **Process and Thread**: Các hoạt động liên quan đến process, thread và việc tải các module.
  - **Network***: các sự kiện mạng mà ProcMon hỗ trợ ghi nhận, chẳng hạn như 1 số hoạt động TCP/UDP
- There are some app that run and shut down in a matter of seconds. It is very difficult to monitor what these app are doing while they are running using standard tools. This is where the ProcMon tool comes in handy(rất tiện dụng).
- Hướng dẫn sử dụng:
  - Bước 1: Khởi chạy ProcMon: truy cập thư mục Sysinternal và chạy ```ProcMon64.exe``` với quyền Administrator
  - Bước 2: Thiết lập Filter để giám sát tiến trình. Để chỉ hiển thị các hoạt động liên quan đến ```wildfire-test-pe-file.exe```, cần tạo Filter (sử dụng Ctrl+L), Filter này yêu cầu ProcMon chỉ hiển thị các sự kiện có đường dẫn file thực thi chứa chuỗi wildfire.
  - Bước 3: Bắt đầu Capture
      - Sau khi thiết lập Filter, nhấn nút **Capture** để bắt đầu ghi nhận các sự kiện.
      - Tiếp theo, thực thi file ```.exe``` trong môi trường máy ảo phân tích được cô lập.
      - ProcMon sẽ ghi nhận những hoạt động diễn ra trong quá trình file thực thi.
  - Bước 4: Phân tích các sự kiện
      - Sau khi chạy file, ProcMon sẽ hiển thị danh sách các sự kiện liên quan: time of day, process name, PID, Operation, Path, Result, Detail
### Process Explorer (ProcExp.exe)
- The Process Explorer is similar to the Windows Task Manager, but provides more information. It is often used by technical users and system administrators.
- Process Explorer displays detailed information about each process, such as memory usage, CPU load, full path of the executed file, open file handles and installed DLLs. It displays processes and their sub-processes in a hierarchical structure, allowing you to understand how a process relates to other processes and which processes are initiated by which processes.

# Sandboxes

# Code Analysis




