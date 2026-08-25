
> [!info] Learning Objectives
> - Hiểu Intelligence là gì.
> - Hiểu Cyber Threat Intelligence (CTI)
> - Hiểu cách tổ chức sử dụng và tạo ra Threat Intelligence
> - Hiểu quy trình Planning & Direction
## Topics

![[Pasted image 20260717111546.png]]
## Course Goal
### Một CTI Analyst có thể:

- Phân tích các cuộc tấn công và thất bại của Threat Actor.
- Xây dựng mô tả về campagin, Threat Actor và Organization.
- Thu thập và khai thác Intelligence từ nhiều nguồn.
- Quản lý Intelligence nhằm phục vụ mục tiêu của tổ chức.
---
### School of Thought

Là một góc nhìn hoặc trường phái tư duy của một nhóm người có cùng phương pháp và quan điểm.

--- 

### I. Understanding Intelligence
#### Case Study: Moonlight Maze
##### Tổng quan
- Chiến dịch Cyber Espionage (1996-1999), nhắm vào Government và Military của Hoa Kỳ, có nhiều dấu hiệu liên quan đến Nga.
##### Investigation
Nguồn dữ liệu:
- HRTest Proxy
- Logs
- Binary
- Connection History
- C2 Activity
Do dữ liệu rất lớn nên cần: Processing, Correlation (tương quan) và Analysis để tạo ra Intelligence.
##### Connection to Penguin Turla
Kaspersky nhận thấy: cùng sử dụng LOKI2, cùng giao thức C2, Target tương tự, Binary cùng thời kỳ.
=> Moonlight Maze có khả năng là tiền thân của Turla
##### Lessons Learned
- Không nên phân tích từng Incident riêng lẻ.
- Phải phân tích theo Campaign
- Artifacts vẫn có giá trị nhiều năm sau.
- Threat Actor cũng cải thiện OPSEC sau mỗi chiến dịch.
- Intelligence cần được chia sẻ để tìm ra pattern qua nhiều mục tiêu.
--- 
##### Intelligence
###### Definition
> Intelligence là quá trình thu thập, xử lý và phân tích thông tin về đối thủ nhằm phục vụ an ninh và hỗ trợ đưa ra quyết định.
##### Intelligence là gì ?
- Không chỉ là Information.
- Vừa là Processs.
- Vừa là Product
##### Intelligence qua các thời kỳ
- Ban đầu: Chính phủ, quân đội
- Hiện nay: Doanh nghiệp, CyberSecurity, Threat Intelligence
##### Data vs Information vs Intelligence
| Data          | Information             | Intelligence                                                     |
| ------------- | ----------------------- | ---------------------------------------------------------------- |
| Raw data      | Có context              | Có phân tích và insight                                          |
| IP, Hash, Log | IP độc, Domain phishing | Đánh giá mức độ ảnh hưởng, Campaign liên quan, Khuyến nghị xử lý |

---
##### Intelligence = Process
Quy trình tạo Intelligence
1. Collect -> 2. Enrich -> 3. Analyze -> 4. Verify -> 5. Disseminate
Ví dụ: RSS -> OSINT -> OpenCTI -> VirusTotal -> Sandbox
---
##### Intelligence = Product

Là **kết quả cuối cùng** của quá trình tạo Intelligence.

Ví dụ:

- Threat Report
- Campaign Analysis
- IOC đã Verify
- Detection Recommendation
- Executive Brief
- Threat Assessment

> [!note]
> Product phải chứa **insight** và **khuyến nghị**, không chỉ là tập hợp dữ liệu.

---
##### Classic Intelligence Sources

| Nguồn | Mô tả |
|-------|------|
| **HUMINT** | Human Intelligence - thu thập từ con người (điệp viên, nguồn tin, phỏng vấn...) |
| **SIGINT** | Signals Intelligence - thu thập từ tín hiệu liên lạc (radio, điện thoại, Internet...) |
| **GEOINT** | Geospatial Intelligence - hình ảnh vệ tinh, bản đồ, vị trí địa lý |
| **MASINT** | Measurement and Signature Intelligence - radar, phổ điện từ, hồng ngoại, dấu hiệu vật lý |
| **OSINT** | Open Source Intelligence - nguồn mở: Internet, báo chí, mạng xã hội, WHOIS, Shodan... |

##### ALL SOURCE Intelligence

Là Intelligence được tạo ra bằng cách **kết hợp tất cả các nguồn** trên để đưa ra đánh giá toàn diện.

Ví dụ:

- OSINT cung cấp Domain.
- SIGINT cung cấp lưu lượng mạng.
- HUMINT cung cấp thông tin nội bộ.
- GEOINT xác định vị trí mục tiêu.

↓

Kết hợp tất cả để tạo **Threat Assessment**.

---
##### Counterintelligence

**Counterintelligence (CI)** là hoạt động:

- Phát hiện (Detect)
- Đánh giá (Assess)
- Vô hiệu hóa (Neutralize)
- Khai thác (Exploit)

các hoạt động tình báo của đối phương.

> [!tip]
> Intelligence tập trung vào **thu thập thông tin về đối phương**.
>
> Counterintelligence tập trung vào **đối phó hoạt động tình báo của đối phương**.

Ví dụ:

- Phát hiện APT đang theo dõi tổ chức.
- Điều tra Insider Threat.
- Phát hiện gián điệp cài cắm trong tổ chức.
- Honeypot để đánh lừa và thu thập thông tin về attacker.

---
##### Sherman Kent

Được xem là **Father of Intelligence Analysis**.

Triết lý nổi tiếng:

> **"Intelligence must be useful."**

Intelligence chỉ có giá trị khi hỗ trợ **ra quyết định**.

---
##### Analysis

Analysis là **trọng tâm của Intelligence**.

Mục tiêu:

Biến **Data → Information → Intelligence**.

Có hai hướng phân tích chính:

###### Data-driven Analysis

- Dựa trên dữ liệu và bằng chứng.
- Dễ kiểm chứng.
- Dễ giải thích.
- Phụ thuộc vào chất lượng dữ liệu.

→ Trả lời câu hỏi:

> **Dữ liệu đang nói gì?**

###### Conceptually-driven Analysis

- Dựa trên kinh nghiệm.
- Framework.
- Bối cảnh.
- Giả thuyết.

Áp dụng khi dữ liệu chưa đủ.

→ Trả lời câu hỏi:

> **Với hiểu biết hiện tại, điều này có thể có ý nghĩa gì?**

---
##### Thinking About Thinking

Analyst cần liên tục kiểm tra cách mình đang suy nghĩ.

Mục tiêu:

- Giảm Bias.
- Tránh kết luận vội.
- Đánh giá nhiều giả thuyết khác nhau.

---
##### Analysis in Action

###### Working Memory

Bộ nhớ ngắn hạn dùng để giữ và xử lý thông tin trong lúc phân tích.

###### Pattern Matching

- **Template Matching:** so khớp với mẫu đã từng gặp.
- **Prototype Matching:** so với mẫu đại diện.
- **Top-down Processing:** dùng kiến thức và bối cảnh để lấp khoảng trống dữ liệu.

###### Bias Control

Luôn tự hỏi:

- Mình đang dựa trên dữ liệu?
- Hay đang suy diễn?

---
##### Structured Analytic Techniques (SAT): Các kỹ thuật phân tích có cấu trúc là phương pháp phân tích thông tin tình báo và đưa ra kết luận.

Một số công cụ hỗ trợ phân tích:

- Brainstorming
- Sorting
- Excel
- Mind Map

Mục tiêu:

- Giảm thiên kiến (Bias).
- Phân tích có hệ thống.
- Đánh giá nhiều khả năng thay vì chỉ một kết luận.
---
[[Exercise I.I Structured Analytic Techniques]]
(**Page 45**)
##### Case Study: Operation Aurora, Elderwood, Shady RAT, Night Dragon và RSA?
=>  Một adversary có thể thực hiện nhiều operation khác nhau, nhắm vào nhiều ngành khác nhau, nhưng để lại pattern có thể liên kết.
=> IOC có thể thay đổi, nhưng pattern về TTP, mục tiêu và cách vận hành thường có giá trị lâu hơn.
### II. Understanding Cyber Threat Intelligence

"Always distinguish which is which" -> that focus on the threat-the human. You must focus on your customer and not just what feels or look cools.
>[!Define]
> Analyzed information about the hostile intent, opportunity, and capability of an adversary that satisfies a requirement.
> - The analysis is on the threat
> - The focus is on the customer

![[Pasted image 20260721145617.png]]
#### **CTI Terminology**
- > **An adversary or threat**:  represent of the human behind the keyboard. It is entity involved in the execution of an intrusion
	- Threat can be established by evaluating (intent+opportunity+capability)

- > **Intelligence requirement**: is question that drives the intelligence life cycle, as a pain point or knowledge gap as it relates to the adversary that an org seeks to satisfy.
	- "A request to satisfy a knowledge gap about the threat or the operational environment"
	- Best practice: Ask only one question, focus on specific fact, event, or activity; support a single decision. 

- > **Intrusion**:  is any successful or failed attempt (nỗ lực dù thành công hay thất bại) của kẻ thù nhằm tổn hại đến hệ thống. 
	- Any successful or failed attempt by the adversary
	- Useful for identifying adversary tradecraft
	- Intusion analysis isds the fundamental CTI Skill
	=> **Core of all cyber threat intelligence**

- > **Intrusion set**: to describe the link of mul intrusion together (thường khi có sự trùng lặp về ioc). Nhóm các intrusion được liên kết với nhau dựa trên điểm chung về kỹ thuật. 
	
- > **an activity group**: set of event and activity tương đồng về features and weighted by confidence scoring. Simply, cluster: adversay, infrastructure, Tradecrafe(Capability/TTP and victim that meets some analytical requirement). Nhóm có nhiều intrusion, nhiều campaign, infra liên quan, malware, target,...
	-  "Diamond Model of Intrusion Analysis" : 1 nhóm các intrusion được gom lại dựa trên các điểm chung (vertices) của Diamond Model
	 ![[Pasted image 20260722113332.png]]
	
- > **Threat actor**: is the threat (person/team/organize)  

- > **A campagin or operation**: adversary's mission focus: malicious group of adversaries taget financial network. 
	- "mission objective of the adversary" - objective (mục tiêu) của 1 chuỗi intrusions hoặc operations.
	- **"Collection Gap"**: khoảng trống trong quá trình thu thập dữ liệu, khiến analyst không có đủ thông tin để nhìn thấy toàn bộ bức tranh.

- > **TLP**: Traffic Light Protocol và là tiêu chuẩn cho info sharing sử dụng: White, Green, Amber, Red để xác định thông tin có thể được chia sẻ với ai. 
	- **"Red"** - thông tin cực kỳ nhạy cảm: không được chia sẻ ra ngoài
	- **"AMBER"** - thông tin nội bộ: chỉ chia sẻ cho tổ chức, cho những người cần biết để xử lý
	- **"Green"** - thông tin cộng đồng: chia sẻ với đối tác hoặc với tổ chức cùng ngành, nhưng không đăng công khai trên Internet.
	- **"White"** - thông tin công khai.

- > **Victim**
- > **Target**: intended victim of an intrusion
- > **Persona**: fake name or identifier that an adversary takes, it can be operated by one or more adversaries operating on the same of different groups.
  => 1 adversary chỉ trở thành threat khi có opportunity - cơ hội tiếp cận hệ thống; Intent - ý định tấn công; Capability - năng lực, kỹ năng và công cụ thực hiện. 
	- Adversary thực hiện các intrusion (xâm nhập - failed/attempt, success/compromise)

- > **TTP**: mục tiêu, kỹ thuật, quy trình

- >**Tradecraft**: kết hợp của methods, capabilities and resources (such as infrastructure) that an adversary leverages (tận dụng). "Cách kết hợp nhiều TTP"
	- Mô tả: "Đối phương thường hoạt động theo phong cách nào?"
	- khác TTP vì không tập trung vào tactic, procedure.

- >**Indicators**: Data + Context 
- >**Indicator Life Cycle Introduction**: 		![[Pasted image 20260722163730.png]]
	- "describes how indicators (or intelligence) beget indicators" - mục đích: 1 indicator sẽ giúp phát hiện nhiều indicator mới
	- **_State_**: 
		- Revealed (Know): indicator vừa được biết -> DBU (discovered by us) or nhận từ TI feed
		- Vetted: indicator phải được verify
		- Mature: sau khi vet xong, indicator được discovery, detection, mitigation
		- Utilized: indicator được triển khai (thực sự match activity)
		- Generate new indicators: sau khi detect, tìm thêm IP, domain, URL,...
	- "**Snowball Effect**": 1 ioc -> 200 ioc 
	- "**Yellow Snowball**": nếu ioc ban đầu sai -> detect -> sinh ioc mới -> share cho người khác -> sai lan rộng

- >**Key Indicators**: ![[Pasted image 20260722165014.png]]
- Một **Key Indicator** là indicator có giá trị cao trong việc phát hiện, theo dõi và phân tích hoạt động của adversary. 
- **Một Key Indicator nên có các đặc điểm sau:** 
	- **Uniquely distinguish an activity group or campaign.** - Có khả năng phân biệt một **Activity Group** hoặc **Campaign** với các nhóm/chiến dịch khác.
	- **Distinguish malicious activity from benign activity.** - Có khả năng phân biệt **hoạt động độc hại** với **hoạt động hợp lệ (benign)**. 
	- **Align to a phase of the adversary's intrusion.** - Gắn với một **giai đoạn cụ thể trong chuỗi tấn công** (Kill Chain/Intrusion Lifecycle), chẳng hạn Initial Access, Execution, Persistence hoặc C2. 
	- **Remain consistent across multiple intrusions.** - Xuất hiện **ổn định và lặp lại** trong nhiều intrusion, không chỉ ở một sự kiện đơn lẻ. 

		 - **Collect as many indicators as possible.** 
		 - **Identify indicators from at least two different attack phases.** 
		 - **Validate indicators across three or more intrusions.** 
##### >Discovery and Indicator Life Span

**Khái niệm**

- Mọi indicator đều có **vòng đời hữu ích (life span)**.
- **Adversary** quyết định vòng đời của indicator, không phải analyst.
- Indicator vẫn có giá trị cho đến khi **không còn hữu ích**.
- Indicator có thể **không xuất hiện trong nhiều năm (dormant)** nhưng vẫn có thể được tái sử dụng.

**Nguyên tắc**

- Chỉ retire indicator khi nó gây **false positives** đáng kể.
- Không xóa indicator chỉ vì đã cũ hoặc lâu không xuất hiện.
- Thiếu tài nguyên tính toán không phải lý do để loại bỏ indicator.

**Điểm cần nhớ**

- Indicator càng **gần adversary** (Tradecraft, Capability, TTP) → vòng đời thường càng dài.
- Indicator càng **dễ thay đổi** (IP, Domain) → vòng đời thường ngắn hơn.

**Key Takeaways**

- Adversary dictates indicator life span.
- Keep good indicators until they become inaccurate or generate excessive false positives.
- Indicators may be dormant for years.
##### Indicator Fatigue and Proper Use Cases

**Indicator Fatigue (Mệt mỏi vì Indicator/Alert)**

- Quá nhiều indicator hoặc alert sẽ làm analyst bỏ sót các cảnh báo quan trọng.
- Indicator là bằng chứng của **các intrusion trong quá khứ**, không phải công cụ phát hiện tốt nhất cho mọi mối đe dọa mới.
- Lạm dụng IOC để detect sẽ làm tăng **False Positives** và **Alert Fatigue**.

**Các trường hợp sử dụng đúng (Proper Use Cases)**

1. **Indicator Sweeps**
   - Tạo indicator từ chính incident của tổ chức.
   - Dùng để tìm các hệ thống bị ảnh hưởng và xác nhận đã xử lý sạch sự cố.

2. **Addressing Knowledge Gaps**
   - Bổ sung kiến thức còn thiếu về adversary.
   - So sánh với các intrusion khác.
   - Pivot sang các nguồn dữ liệu khác để điều tra.

3. **Enrichment**
   - Dùng để làm giàu dữ liệu trong SIEM hoặc các tập dữ liệu lớn.
   - Không nên dùng làm nguồn phát hiện chính.

**Key Takeaways**

- Indicator có giá trị nhất khi **được tạo từ chính môi trường của tổ chức**.
- Không nên phụ thuộc hoàn toàn vào IOC từ Threat Intelligence Feed.
- Giá trị lớn nhất của indicator là:
  - Incident Scoping
  - Knowledge Gap Filling
  - Data Enrichment

##### Case Study: PROMETHIUM and NEODYMIUM
###### Background
- **PROMETHIUM**: được quan sát từ 2012, có tradecraft riêng biệt so với NEODYMIUM
	- Sử dụng: (Truvasys) Malware first-stage, ngụy trang thành các tiện ích máy tính phổ biến như WinRAR -> Delivery: gửi link qua instant messenger dẫn nạn nhân tới mal document -> khai thác cve-2016-4117 trước khi lỗ hổng được công khai. 
- **NEODYMIUM**: quan sát từ 2016
	- Wingbird malware -> Delivery: highly tailored spear-phishing email + attachment (các attach RTF document và cũng khai thác CVE-2016-4117)
=> Vị trí nạn nhân tương tự, thời điểm hoạt động tương tự và sử dụng cùng 1 zero-day exploit trước khi lỗ hổng được công khai.                                         
![[Pasted image 20260724170130.png]]
=> Khi nhiều intrusion thể hiện các pattern đủ đặc trưng trên hai hoặc nhiều vertex (đỉnh) của Diamond Model, analyst có cơ sở cluster chúng thành 1 **Activity Group** "Two vertices or more as unique clusters in the intrusions are required to declare a cluster of intrusions an Activity Group" - "Overlap between Activity Groups is perfectly acceptable:": 2 activity group được phép có đặc điểm chung. 
###### 4 ý cần nhớ:
- Activity Group = cluster of related intrusion activity, không nhất thiết đồng nghĩa với 1 threat actor đã attribution
- Diamond Model có Adversary-Capability-Infrastructure-Victim
- Overlap giữa Activity Groups là bình thường; cùng CVE/victim không chứng minh cùng actor
- Việc cluster/tách Activity Group phải có giá trị cho defender; giúp xác định đúng TTP, infrastructure, victim relevance và defensive actions. 

### III. Threat Intelligence Consumption

![[Pasted image 20260727164402.png]]
#### **Intelligence Generation là gì?**
- **Generation -> Intrusion Analysis + Strategic Value** (phía tạo ra intelligence từ dữ liệu/thông tin về threat)
- Các framework/model đã học:
	- Intelligence Life Cycle
	- Cyber Kill Chain
	- Diamond Model
- Chúng giúp analyst:
	- Phân tích intrusion
	- Hiểu adversary
	- Liên kết nhiều intrusion
	- Nhận diện campaign
	- Hiểu TTP
	- Tạo ra assessment/intelligence có giá trị
*Example: Generation analyst không chỉ nói "Có IP X và hash Y" mà phân tích phishing-> Powershell...Sau đó dùng Diamond Model, Kill Chain, ATT&CK để tạo context và assessment*.
#### Intelligence Consumption là gì?
- **Consumption -> Defense-focused + Organization-specific** (đưa Intelligence vào sử dụng để bảo vệ tổ chức) -> Cần analyst hiểu: **Threat + chính env của tổ chức** (Know thyself and know the adversary)
- Consumption được đưa vào phòng thử ntn?
	- ##### **_Passive defenses_**: không cần con người liên tục tương tác (firewall, anti-malware, IDS/IPS,...) *eg: mal IP -> fw block, AV/EDR detect*.
	- ##### **_Active defenses_**: Intelligence được con người/team sử dụng trực tiếp:
		- Network Security Monitoring analysits
		- Malware analysts
		- Incident Responders
		- SOC
		- *eg: SOC nhận được TI: APT X sử dụng powershell+scheduled task+domain Y -> SOC sử dụng info đó để threat hunt trong env: search telemetry, find suspicious powershell, invest endpoint..*
=> **Mối quan hệ**: Generation -> <- Consumption: những người sử dụng intelligence cũng tạo ra dữ liệu rất có giá trị cho những người tạo intelligence.
> [!Note]
> **Generation asks: “What does this threat mean?”**  
>**Consumption asks: “What does this threat mean to us, and what should we do about it?”**

#### Sliding Scale of Cyber Security
###### Sliding Scale of Cyber Security gồm 5 nhóm:
Architecture -> Passive Defense -> Active Defense -> Intelligence -> Offense

| Thành phần          | Hiểu đơn giản                                                                                                | Ví dụ                                                                                  |
| ------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| **Architecture**    | Xây hệ thống sao cho khó bị tấn công ngay từ đầu                                                             | Secure architecture, patching, supply-chain security, network segmentation, hardening. |
| **Passive Defense** | - Các hệ thống tự động bảo vệ/phát hiện (không yêu cầu con người tương tác)<br>- Marking the static flexible | Firewall, IPS, AV, EDR, SIEM rule                                                      |
| **Active Defense**  | Con người chủ động tìm kiếm và phản ứng threat                                                               | Threat hunting, IR, NSM, malware analysis                                              |
| **Intelligence**    | Thu thập → phân tích → tạo intelligence về adversary                                                         | CTI                                                                                    |
| **Offense**         | Chủ động tác động vào adversary (các hành động trực tiếp chống lại adversary)                                | Takedown, legal countermeasures...                                                     |

=> Sliding Scale là framework để thảo luận cybersecurity activities, không phải maturity model -> Nó chỉ phân loại hoạt động cybersecurity
##### Leverage Intelligence to Drive value  
- Architecture ← Passive ← Active ← Intelligence: intelligence thu thập ở phía bên phải tạo ra thay đổi ở bên trái
> Intelligence should drive change toward the left side of the Sliding Scale whenever possible. (thúc đẩy thay đổi về phía bên trái của scale)

"ROI: RETURN ON INVESTMENT"
-> Offense # Active Defense và Threat hunting là Active Defense, không phải offense
##### Intelligence có thể được consume để cải thiện chính intelligence
- Intelligence có thể được dùng cho:
	- Adversary Emulation: dùng knowledge về TTP của adversary để **mô phỏng** hành vi của chúng.  (APT X -> Spear phishing -> Powershell -> Credential dump -> RDP lateral movement)
		- Red Team # Pentest (red team không cần chạy "tool mới nhất" mà mô phỏng tradecraft thực sự của threat liên quan tới tổ chức) 
	- Hypothesis Generation: "Nếu adversary X tấn công chúng ta, chúng có thể sử dụng Powershell sau khi compromise VPN"
	- Team Restructuring: cấu trúc/team không phù hợp với threat mà tổ chức đang đối mặt
##### **Four types of threat detect**
- Environment vs Threat
- Knowns vs Unknowns
-> Configuration Analysis – Modeling – Indicators – Threat Behaviors

|              | Environmental              | Threat               |
| ------------ | -------------------------- | -------------------- |
| **Unknowns** | **Modeling**               | **Threat Behaviors** |
| **Knowns**   | **Configuration Analysis** | **Indicators**       |
Tức là analytic nên giúp analyst hiểu:

```
What happened?
      +
Why is it suspicious?
      +
What threat behavior might this represent?
      +
What should analyst investigate next?
```

##### The Pyramid of Pain - kim tự tháp nỗi đau
> [! Pyramid of Pain] 
> Pyramid of Pain là mô hình dùng để thể hiện mức độ khó khăn mà defender gây ra cho adversary khi phát hiện và ngăn chặn các loại indicator khác nhau.
> -> Dùng để phân loại indicator (mức độ "đau đớn" mà adversary phải chịu khi defender phát hiện và tạo cảnh báo dựa trên các indicator ở từng tầng).

![[Pasted image 20260728163326.png]]

| Mức | Loại indicator             | Mức độ khó đối với adversary                        |
| --- | -------------------------- | --------------------------------------------------- |
| 1   | **Hash Values**            | Rất dễ thay đổi – _Trivial_ (gần như không đáng kể) |
| 2   | **IP Addresses**           | Dễ thay đổi – _Easy_                                |
| 3   | **Domain Names**           | Khá đơn giản để thay đổi – _Simple_                 |
| 4   | **Network/Host Artifacts** | Gây khó chịu – _Annoying_                           |
| 5   | **Tools**                  | Khó thay đổi hơn – _Challenging_                    |
| 6   | **TTPs**                   | Rất khó thay đổi – _Tough_                          |
- Indicator càng thấp càng dễ detect nhưng cũng dễ bị attacker thay đổi. 
- Indicator càng cao càng khó detect nhưng có giá trị phòng thủ lâu dài hơn. 
- Hash/IP/domain phù hợp với block, triage và incident scoping. 
- Network/host artifacts, tools và TTPs phù hợp với behavioral detection. 
- TTPs gây nhiều khó khăn nhất vì attacker phải thay đổi gần như toàn bộ cách hoạt động.
- Không nên chỉ thu thập IOC; cần dùng IOC và intrusion context để xây behavioral analytics.
[[Exercise I.2 Lead-In]]



### IV. Positioning the Team to Generate Intelligence
### V. Planning and Direction
