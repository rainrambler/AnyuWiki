- [[Matter]] 协议的安全性描述
- Matter 协议基于 [[TCP]]和[[UDP]]，传输层基于[[IPv6]]，底层支持 [[Wi-Fi]]、Thread、[[BLE]] （Commissioning only. 仅用于委托或试运行？）、[[Ethernet]]等。
- 安全**威胁**：
	- 用于远程控制的产品的错误功能
	- [[DDoS]]攻击
	- 数据和隐私泄露
	- 知识产权偷窃
	- 潜在损害人身安全
- 移动通信和联网设备的**安全机制**可用：
	- 设备实体证明或设备来源证明
	- 安全通信
	- 访问控制
- 在智慧家庭中部署安全的**关键方面**：
	- 制造：工厂或者供应链的攻击来源。如恶意代码注入（ [[Code injection]] ）
	- 运营：远程攻击和物理攻击
	- 维护：生命周期的维护机制对安全很重要；安全的软件更新流程，避免加载恶意软件。
- 常用的最佳实践：
	- 安全制造：设备实体证明、可信固件
	- 安全通信和运营：通信的加密和认证。注意包含单播和多播。确保数据流到达指定的目标，保护[[CIA]]属性。
	- [[OTA]] 更新
	- 安全监管：每个国家都不同，且持续变化。需要一定的提前设计。
- 安全设计原则
	- **全面性**（Comprehensive，分层防御，layered approach）
	- **健壮性**（Strong）：使用严格测试的密码学标准算法。
		- 如 [[ECC]] [[NIST]] P256和AES-CCM-128. [[AES]]-[[CCM]]用于保障机密性和完整性。AES-CTR用于保护标识符，以保障隐私。[[SHA-256]] 保护完整性；ECC [[secp256k1]] 曲线用于数字签名([[Digital signature]])和密钥交换([[Key exchange]])、密钥派生以及随机数生成 [[RNG]] 。
		- 在此基础上，基于 [[Passcode]] 的会话、基于证书的会话建立协议，用于上线、取证和操作。
		- Matter要求设备证明（[[Device attestation]]），否则无法加入Matter总线（fabric）。
		- Matter扩展了CSA 分布式合规链技术，提供全球的互操作平台[1]。
	- **易用性**：易于制造和使用。
		- 核心标准包含样例和测试向量集。 [[GitHub]]开源。
	- **韧性**：包含保护、检测和恢复（Protect, Detect and Recover）
	- **敏捷性**：密码算法敏捷度
- 隐私保护原则
- 数据隐私被嵌入到Matter中，是所有协议和互动方法的核心概念。
- **核心原则：**
	- 合法性、公平性和透明度
	- 目的限制
	- 数据最小化
	- 准确性
	- 存储限制
	- 网络安全（完整性和保密性）。
	- 负责任
- 完全遵守这些原则不仅需要对Matter标准协议的支持，还需要Matter设备生活和运行的所有支持环境和基础设施。这是因为数据隐私要求旨在保护其数据被相关系统消费和交易的个人隐私，而Matter协议在设计上并不直接处理与人相关的信息，而只是处理关于和来自交互设备和软件代理的信息。然而，对于所有可能通过关联或推理与个人信息间接相关的数据，Matter协议在Matter相关设备互动的边界内坚持上述所有原则：
	- Matter设备之间的所有数据通信具有当前民用网络通信标准所支持的最高级别的保密性和完整性。这确保未经授权的实体不能轻易窃听或篡改物质设备之间的通信数据。
	- 所有的Matter设备都需要通过证明密钥对(attestation keypair)和由可信CA签署的x.509认证来提供身份证明，以便数据只在已知的Matter实体之间共享。
	- Matter是一个开放的标准，能够对其包括的协议和安全控制进行同行审查和验证，包括合法的Matter设备之间的互动。
	- 所有在Matter互动中共享的数据都是Matter协议正确和稳健运行所需的最小数据。在Matter的设计中，我们非常注意尽量减少需要在节点之间共享的信息量，从而将无意中泄露信息的可能性降到最低。
	- 按照标准的规定，Matter节点之间共享的所有数据都是严格按照规定的目的进行的，如建立互动各方的身份，为连续操作创建安全的相互背景或关联，相互同意的互动模式等。所有与Matter协议层以上设备的具体操作有关的数据都可能影响数据隐私，但不在Matter范围内。
	- Matter通过在核心规范中纳入许多保护隐私的机制来解决隐私问题，如唯一的随机节点标识符、具有可配置隐私的会话建立、不可追踪的IP地址和具有私人消息头的会话。具体来说，当同一结构内的实体通过网络进行通信时，它们在消息中的节点标识（通常是透明的）可以选择使用单独的加密密钥进行加密，该密钥是为会话协商的。这确保了任何在网络上偷听的人，除了由于消息加密而无法阅读消息之外，也无法看到通信各方的身份。
- [1] https://spectrum.ieee.org/forget-cryptocurrencies-and-nftssecuring-devices-is-the-future-of-blockchain-technology
- Ref:
- https://csa-iot.org/wp-content/uploads/2022/03/Matter_Security_and_Privacy_WP_March-2022.pdf