---
layout: post
title: "Part 2: Analyzing File Structure"
date: 2026-10-06
description: "Part 2: Analyzing File Structure"
---

# Analyzing File Structure
- The first step in static analysis is the examination of the file structure of the malware.
- Basic characteristics such as file extension, size and file signature help to determine the file type. Any files or malicious code hidden within the malware are also examined at this stage.
- After compilation, files are refered to as "executable" files.
- There are different types of exe files, and their structures vary depending on the OS.

## Executable Files
- The PE (Portable Executable) file format is designed for Windows OS and is typically used in executable files (.exe), dynamic link libraries (.dll) and other system files (.sys) on Windows. 
- ELF (Executable and Linkable Format) is a file format used primarily in Unix and Unix-like operating systems (Linux, Solaris, FreeBSD và others). The ELF file format provides a standard format for many different types of files, such as executable files, object files, shared libararies and kernel modules. 
- The easiest way to see what type of file an execuatle to use the ``` file ``` command in Linux:
  ``` file putty.exe ```

<img width="1896" height="248" alt="image" src="https://github.com/user-attachments/assets/1c7336fb-0804-455a-ace8-de3e8f26b484" />

  - **ELF 64-bit LSB**: ELF is a format used by Unix and Unix-like OS. The "64-bit" signifies that the file is created for 64-bit, while "LSB" (Least Significant Byte) shows that   the byte order is "little-endian" (binary sử dụng **little-endian** tức byte có trọng số thấp được lưu trước trong bộ nhớ).
  - **pie executable**: PIE (Position Independent Executable): chương trình được biên dịch để không phụ thuộc vào 1 địa chỉ base cố định trong memory. Ví dụ, nếu không có PIE, 1    executable có thể thường xuyên được load quanh: 0x400000 nhưng với PIE, hệ điều hành có thể load ở những vị trí khác nhau, lần 1,2,3. Điều này cho phép **ASLR (Address Space      Layout Randomization)** random hóa vị trí của executable trong memory
  - **interpreter/lib64/ld-linux-x86-64.so.2**: trình thông dịch, sử dụng .so.2 làm trình liên kết động, cần thiết để tải và thực thi các file ELF.
  - **stripped**: một số thông tin symbol/debug không cần thiết để chương trình chạy đã bị loại bỏ khỏi binary.

## PE File Structure
- **DOS Header**: all PE files start with a simple DOS MZ header để đảm bảo khả năng tương thích với các hệ thống DOS cũ. This includes a specific signature that identifies the file as a PE file.
- **PE Header**: marks the beginning of the actual PE file and contains basic information about the file. For example, the machine type and the number of sections are included in this area.
- **Section Headers**: contains inforamtion about the sections within the file. Each section header includes details such as the size, location and access permissions of the section.
- **Sections**: Various sections such as code, data, and resources contain the executable code, data, and resources of the file. These sections are the content that will be used at runtime.
- **Import Table**: This table indicates which functions the PE file uses from other files. It typically includes system calls or other library funtions. File này cần dùng gì từ bên ngoài? Chứa danh sách các hàm mà PE gọi từ DLL/thư viện khác.
- **Export Table**: Lists the function and other symbols exported by the file. This indicates the functions that can be used by other programs or libraries. File này cung cấp gì cho bên ngoài? Chứa các hàm mà PE cho phép chương trình/DLL khác gọi. Đặc biệt hay gặp khi phân tích DLL. Ví dụ, DLL export ``` init, HttpMain, Start ``` thì chương trình khác có thể gọi hàm này.
- **Resource Section**: Contains user interface elements such as icons, menus, and dialog boxes for the application. File mang theo tài nguyên gì? Chứa dữ liệu được nhúng bên trong PE, thường là icon, ảnh, menu, dialog, version info...Malware có thể giấu config, payload hoặc binary khác trong resource.
PE files can be analyxed with any "hex editor" program

