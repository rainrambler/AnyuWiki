- Remote Key Provisioning
- 从安卓12开始，谷歌正在用厂内公钥提取和空中证书配置（短期证书）的组合来取代厂内私钥配置。
- #Android 13将要求这个方案，它有几个好处。首先，它可以防止OEM和ODM需要在工厂里管理密钥保密性。其次，如果设备的密钥被泄露，它可以恢复设备，这意味着消费者不会永远失去对受保护服务的访问权限。
- 现在，在使用需要证明的服务时，向谷歌申请一个临时证书，而不是使用设备上的密钥计算出来的证书，该证书可能会通过漏洞泄露。
- 每个设备都会生成一个独特的静态密钥对，该密钥对的公共部分由OEM在其工厂中提取并提交给谷歌的服务器。在那里，它们将作为以后配置的信任基础。私钥永远不会离开生成它的安全环境。
- 当设备第一次连接互联网时，它将为其生成的密钥生成一个证书签名请求，用与工厂收集的公钥相对应的私钥进行签名。谷歌的后端服务器将验证该请求的真实性，然后签署公钥，返回证书链。然后，设备上的密钥库将存储这些证书链，每当要求证明时，就将它们分配给应用程序。要求证明的应用可以是谷歌支付或Pokemon Go。
- 这种确切的证书请求链将在证书过期或当前密钥供应耗尽时定期发生。每个应用程序都会收到不同的证明密钥，而且密钥本身也会定期轮换，这都能确保隐私。此外，谷歌的后端服务器是分段的，这样验证设备公钥的服务器就不会看到所附的证明密钥。这意味着谷歌不可能将证明密钥与请求它们的特定设备联系起来。
- https://www.xda-developers.com/google-remote-key-provisioning/
- 据谷歌称，最终用户不会注意到任何变化，但开发人员需要注意以下内容：
- 证书链结构
	- 由于新的在线供应基础设施的性质，链长度比以前更长，并且可能会发生变化。
- 信任之根
	- 信任根最终将从当前的 [[RSA]] 密钥更新为 [[ECDSA]] 密钥。
- RSA 证明弃用
	- [[KeyMint]] 生成和证明的所有密钥都将使用 ECDSA 密钥和相应的证书链进行签名。以前，非对称密钥由其相应的算法签名。
- 短期证书和证明密钥
	- 为设备提供的证书通常在到期和轮换前最多有效期为两个月。
-