---
layout: post
title: "Part 1: Static Analysis"
date: 2026-10-06
description: "Part 1: Static Analysis"
---
# Static Analysis
- Static Analysis is one of the fundamental steps in malware analysis and is a technique used to examine malware.
- It involves analyzing: malware's file structure, content and actions.
- It is usually the first step in the malware analysis process.
# Compiling
- "Compiling" is the process of translating software source code into machine language that a computer can understand.
- a "compiler": trình biên dịch, convert high-level language into a lower-level or directly into machine code.
- This process consists of stages:
  - **Lexical Analysis**: compiler reads code and converts into meaningful tokens -> ensures source code is read syntactically correctly (đọc đúng về mặt cú pháp)
  - **Syntax Analysis**: rules that represents logical structure of the code
  - **Semantic Analysis**: type checking, helping eliminate logical errors (kiểm tra ngữ nghĩa của expression in the tree structure)
  - **Optimization**: to allow the program to run faster or use fewer resources
  - **Code Generation**: at this point, all the code has been converted to machine language
      - Performace: Converting human-readable source code to machine code is called "**compiling**", while converting machine code back to human-readable is referred to as                "**reversing**". Once code has been transformed from machine to human form, it can never returin to ít orginal state.
      - Security
      - Independence
**In summary**, compiler is informed about wich CPU, architecture, and operating system the copiled code should run on, and allow the same source code to be compiled for different targets on the same machine.
# Debugging
- Debugging is the process used in software development to identify and fix errors or "bugs".
- Programmers execute code step by step and monitor the app's state to detect and resolve issues within the software
    -**Monitor Code Flow**: follow step by step. This enables to see under what conditions the app fail or exhibits unexpected behavior.
    -**Variables and Memory Management**: quản lý biến và bộ nhớ
    -**Breakpoints and Watchpoints**: Điểm dừng và theo dõi at specific lines of code, to be more clearely identified
# Packing
- Executable packing is a method of compressing and encrypting the exe file of software to reduce its size, improve loading times, or enhance security and protection.
- Functions of Executable Packing:
    - Reducing File Size
    - Improving Load Time: can speed up app load times by reducing the time it takes to read from disk
    - Security and Protection: making the process of re more difficult
## Packing Methods
- Shellter
- UPX: open-source nature and flexibility
- The Enigma Protector: designed to protect legitimate software, but also used to make malware analysis more difficult
- MPRESS, Exe Packer 2.300, ExeStealth, Morphine (known for ít unique PE loader and the ability to create unique decoders for each malware sample)
- Themida: Designed to protect Windows applications from tampering, but can also be used to encrypt malware.
- MEW: Uses the LZMA algorithm to compress small malware files.
- FSG: Used to compress both small and large files, but is relatively easy to extract.
- PESpin: Targets Windows code to prevent files from being fixed or distributed.
- Andromeda: Refers to both a botnet and a specific packer, leading to increased reverse engineering efforts.
- VMProtect: Can encrypt a wide range of files without decrypting them on execution by working on virtualized code.
- Obsidium: Can encrypt, compress, and hide code for 32-bit and 64-bit Windows applications.

