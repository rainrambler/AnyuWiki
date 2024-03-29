- [[Keystore]]提供了一个更安全的位置，让您能够以可控方式创建、存储和使用加密密钥。如果有硬件支持的密钥存储区可用，则使用该存储区比从设备中提取密钥材料更安全，并且 [[Keymaster]]强制执行的限制会更难以打破。
- 不过，仅当已知 Keystore 密钥位于由硬件支持的存储区中时，才能够实现这一点。在 Keymaster 1 中，应用或远程服务器无法可靠地验证是否属于这种情况。Keystore 守护程序加载可用的 Keymaster HAL，并相信 HAL 对于密钥硬件支持的任何判断。
- 为了解决此问题，Keymaster 在 [[Android 7]] (Keymaster 2) 中引入了密钥认证，在 [[Android 8]] (Keymaster 3) 中引入了 ID 认证。
- 密钥认证旨在提供一种方式，让您可明确地确定某个不对称密钥对是否由硬件支持、该密钥有哪些属性，及其具有哪些使用限制条件。
- 通过 ID 认证，设备可以提供其硬件标识符（例如序列号或 IMEI）的证明。
- https://source.android.google.cn/security/keystore/attestation
- ID 认证
	- #Android 8.0 为使用 Keymaster 3 的设备提供了对 ID 认证的可选支持。通过 ID 认证，设备可以提供其硬件标识符的证明，例如序列号或 IMEI。虽然这是可选功能，但强烈建议所有 Keymaster 3 实现提供对该功能的支持，因为能够证明设备的身份可确保真正的零触摸远程配置等用例更加安全（因为远程端可以确定与它进行对话的是正确的设备，而非假冒其身份的设备）。
	- ID 认证的工作原理如下：在设备出厂之前，创建只有可信执行环境 ([[TEE]]) 才能访问的设备硬件标识符的副本。用户可以解锁设备的引导加载程序，并更改系统软件以及 Android 框架所报告的标识符。由 TEE 保存的标识符的副本不会以这种方式被操控，这样可确保设备 ID 认证仅用于证明设备的原始硬件标识符，从而阻止尝试假冒身份的操作。
-
- [[Android 14]]
- 密钥证明是为了证明密钥物料早安全的硬件环境中生成和存储；
- 证明记录是 X.509格式的证书链，叶节点包含公钥和属性。
- 属性包括安全硬件、验证启动状态、厂商和启动补丁等级
- 根密钥由 Google 签发
-
- 密钥证明的基础保障：APP在GMS设备上生成基于硬件的密钥时，[[KeyMint]]提供的证明记录保障：
	- 由合法 GMS 设备签发
	- 密钥不可离开设备
	- 密钥有特定的使用限制。由[[Keystore]]和KeyMint保障；
	- 设备的状态，由证明记录表示，是精确的；
-
- 密钥证明的重要性
	- 设备完整性的信号
		- 是否是真实设备
		- 包含安全硬件在内的设备状态
		- 在 Android T及以上版本适用
	- 防止Google服务的滥用
		- 自有服务的安全
		- 第三方开放：Play Integrity API, [[SafetyNet]] Attestation API
		- 企业终端（通过ID证明）
-