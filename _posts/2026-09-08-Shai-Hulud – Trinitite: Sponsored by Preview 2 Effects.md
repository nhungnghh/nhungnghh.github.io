---
layout: post
title: "Shai-Hulud – Trinitite: Sponsored by Preview 2 Effects"
date: 2026-09-08
description: "Chuỗi thực thi nhiều stage của gói npm độc hại infostealer/Shai-Hulud."
---
# Tổng quan
Chiến dịch là 1 multi-stage malware chain nhắm vào hệ sinh thái npm/Node.js, trong đó attacker cố tình chia payload thành nhiều lớp:

```python
obfuscation -> encrypted payload -> runtime decryption -> core logic -> modular payloads -> GitHub-based retrieval -> alternate payload path
```

<img width="1226" height="1283" alt="image" src="https://github.com/user-attachments/assets/18830432-667b-4229-a340-7795a59e557e" />

## Bắt đầu từ package npm bị cài vào hệ thống
Malicious code được phân phối thông qua 1 package trên npm registry
```python
Registry: npm
Type: Infostealer/ Shai-Hulud
Affected Package: @tnohe/openapi-react-query-codegen >3.0.2
```
Sypply-chain attacker là người dùng không chủ động tải malware, người dùng đơn giản đang chạy ```npm install <package> ``` nhưng npm package có thể chứa script:
```
"script": {
  "preinstall": "...",
  "install": "...",
  "postinstall": "..."
}
```
## 1. Stage 1 - Obfuscated Payload
Stage 1 trong sơ đồ được gọi là ```Obfuscated Payload``` tức payload đầu tiên đã tồn tại trong package, nhưng source code bị cố tình làm rối. Trong sơ đồ ta thấy các mảng số kiểu: ```[140,104,122,102,117,106,...]``` - đây có thể là byte array, encoded characters, encrypted bytes hoặc transformed string table. Stage 1 chưa phải malware logic hoàn chỉnh, nó giống 1 "container" hoặc "wrapper" che giấu stage tiếp theo.
### "Obfuscate" và "Encryption"
Attacker đang sử dụng 2 lớp bảo vệ khác nhau:
- Obfuscation: mục tiêu là làm code khó đọc nhưng vẫn có thể thực thi.
- Encryption mạnh hơn Payload có thể là 1 block binary/string hoàn toàn không có ý nghĩa. Muốn chạy được attacker phải: ```encrypted data -> decrypt(key,iv) -> plaintext JavaScript```
-> Encryption giúp attacker tránh detection
Giả sử payload cuối cùng là:

```JavaScript
stealNpmToken();
stealGithubToken();
uploadCredentials();
```
Nhưng nếu payload thực nằm trong: ```encryted blob``` thì static scanner chỉ thấy ```U2FsdGVkX1+....``` hoặc ```[140,104,122,102,...] ```
Payload thật chỉ xuất hiện trong **memory sau khi chương trình chạy**. Đó là lý do runtime analysis/sandbox quan trọng.

## Stage 2 - Encrypted Payload
Sau khi Stage 1 deobfuscate, kết quả là ```Encrypted Payload```. Stage 2 giống 1 encrypted container.
```JavaScript
(async()=>{try{
const _c=await import("node:crypto")
```
Đây là 1 dynamic import: await import("node:crypto") là module crypto tích hợp trong Node.js. Nó hỗ trợ: AES, RSA, SHA, HMAC, random bytes, encryption/decryption. Trong chain này, nó được đặt ngay tại: ``` Decrypt Payload ```
Nên sẽ dùng cypto API của Node.js để giải mã Stage 2.
```JavaScript
const crypto = await import("node:crypto");
const decipher = crypto.createDecipheriv(
    algorithm,
    key,
    iv
);
let payload = decipher.update(data);
payload += decipher.final();
```
Sau đó:
```JavaScript
eval(payload);
```
hoặc:
```JavaScript
new Function(payload)();
```

## Stage 3 - Shai-Hulud Logic
Sau khi decrypt thì đây mới là lúc **core malware logic** xuất hiện. Hay nói cách khác thì Stage 1 = wrapper, Stage 2 = encrypted container, Stage 3 = actual malware. Stage 3 là trung tâm điều phối các stage sau, giải mã payload ở Stage 2 thành mã JavaScript thật sự rồi chuyển quyền thực thi sang logic Shai-Hulud.
```python
"Trinitite: Sponsored by
Preview 2 Effects"
New Public Keys
```
String này có thể là marker, campaign signature, version marker, developer string,...giúp researcher phân biệt variant.
> **Stage 3 là nơi bootstrapper/loader ban đầu chuyển quyền thực thi sang logic thực sự của Shai-Hulud**.

## Stage 4 - Thả 12 payload/module
Malware tiếp tục ```Unload 12 Payloads/ Files```. Thực tế là nó extract/drop/triển khai 12 thành phần có chức năng:
- Memory Dump
- Bun Install
- Token Monitor
- Claude Hooks
- GitHub Pyload Dropper
No hoạt động giống kiến trúc module, mỗi module có nhiệm vụ riêng.
### Memory Dump
Liên quan đến việc đọc hoặc dump dữ liệu trong memory để tìm: token, credential, secret, session information, process data,..dump LSASS, phục vụ **memory dumping/collection**
### Bun Install
```Bun``` là 1 JavaScript runtime/toolchain.
Một module liên quan đến Bun dùng để:
- Kiểm tra Bun
- Cài Bun
- Sử dụng Bun để thực thi JavaScript
- Chuẩn bị runtime cho payload tiếp theo
Do đó attacker không nhất thiết phụ thuộc hoàn toàn vào Node.js.
### Token Monitor
Nó có thể theo dõi hoặc token/secret như: APT token, GitHub token, npm token, cloud credential, developer secrets.
Đặc biệt với supply-chain attack npm, việc chiếm được token developer gây rủi ro lớn, cơ chế giúp một supply-chain campaign có thể tự lan rộng.
``` Compromise developer -> steal npm/Github token -> access repositories/packages -> modify another package -> publish malicious version -> infect more developers ```
### GitHub Payload Dropper
Module này thực hiện:
```
Search GitHub
"1nggatr1n"
```
Tức là malware tìm kiếm 1 identifier/string nào đó trên GitHub. GitHub là dịch vụ hợp pháp nên traffic ít đáng ngờ hơn kết nối trực tiếp tới 1 C2 domain mới đăng ký. Lợi dụng kỹ thuật **living-off-trusted-service / abuse of legitimate service**
```
github.com
raw.githubusercontent.com
```

## Stage 5 - Download ```setup.py```
GitHub Dropper tìm thấy payload rồi tải ```setup.py```, đóng vai trò downloader/stager tiếp theo.
```setup.py``` vốn là file hợp pháp trong ecosystem Python. Bình thường dùng để install Python package nhưng attacker có thể lợi dụng nó như 1 script executable.

## Stage 6 - setup.py tải ```index.js```
Sau khi ```setup.py``` chạy: download Payload ```index.js```. Attacker có 1 implementation khác của payload ban đầu. Sau đó ```index.js``` thực thi qua pattern quen thuộc, stage 5-6 là phiên bản khác của Stage 1-3.

# Kết luận
> Chuỗi thực thi bắt đầu từ 1 package npm chứa JavaScript bị obfuscate. Sau khi được giải mã lớp obfuscation, mã độc khôi phục 1 payload đã mã hóa và sử dụng module ```node:crypto``` để giải mã động tại runtime, qua đó kích hoạt logic chính của Shai-Hulud. Malware sau đó triển khai nhiều module phục vụ thu thập dữ liệu và credential, bao gồm memory dumping, token monitoring và GitHub payload dropper. Thành phần dropper tìm kiếm nội dung do attacker kiểm soát trên GitHub để tải các stage bổ sung như ```setup.py``` và ```index.js```. Các stage sau tiếp tục sử dụng cơ chế obfuscation và encryption tương tự nhằm che giấu 1 biến thể khác của Shai-Hulud, mặc dù nhawnsh này được researcher đánh dấu là chưa được weaponize tại thời điểm phân tích. 
