---
layout: post
title: "Part 3: Manalyze and IDA"
date: 2026-10-06
description: "Part 3-4: Manalyze and IDA - DLL and Functions for Windows"
---

# Manalyze
- Là công cụ hỗ trợ static analysis file PE (Windows executable) tự động. 

# IDA
- IDA free is a disassembler tool for Linux, MacOS, and Windows.

# Import DLLs and Function for Windows
- This lesson will discuss the commonly used DLLs and their functions.
- The most frequently used DLL and functions inherent to the Windows OS:
  - **ADVAPI32.dll**
  - **KERNEL32.dll**
  - **USER32.dll**
  - **WININET.dll và WS2_32.dll**

## ADVAPI32.dll
- **"RegCreateKeyEx", "RegOpenKeyEx", "RegSetValueEx", and "RegDeleteKey"**: Functions that manipulate registry keys. Malware often uses registry keys to ensure persistence or change system settings.
- **"OpenSCManager", "CreateService", "StartService"**: Functions that interact with services. Malware can add itself as a service to the system or modify existing services.
## KERNEL32.dll
- **"CreateProcess", "TerminateProcess"**: Funtions used for process management. Malware may try to start or terminate other processes.
- **"WriteFile", "ReadFile"**: Functions for file reading and writing. These can be used for data theft or to damamge data.
- **"VirtualAlloc", "VirtualProtect"**: Functions related to memory management. Malware can alter the memory settings of running processes to execute malicious code.
## USER32.dll
- **"SetWindowsHookEx", "SendMessage"**: Functions used to monitor user input or interfere with other applications
- **"EnumWindows", "GetWindowsText"**: Funtions used to list open windows and retrieve windows titles.
## WININET.dll and WS2_32.dll
- **"InternetOpen", "InternetConnect", "HttpSendRequest"**: Functions to send and receive data over the network. Malware typically uses these functions to communicate with command-and-control (C&C) servers.
- **"socket", "connect", "send", "recv"**: Functions for low-level network operations. These can be used to create network traffic or steal data.

# Tệp ELF
