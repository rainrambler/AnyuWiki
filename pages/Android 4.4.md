title:: Android 4.4

- **通过 SELinux 得到增强的 Android 沙盒。** Android 现在以强制模式使用 [[SELinux]]。SELinux 是 Linux 内核中的强制访问控制 ([[MAC]]) 系统，用于增强基于自主访问控制 ([[DAC]]) 的现有安全模型。这为防范潜在的安全漏洞提供了额外的保护屏障。
- **按用户应用 VPN。** 在多用户设备上，现在按用户应用 [[VPN]]。这样一来，用户就可以通过一个 VPN 路由所有网络流量，而不会影响使用同一设备的其他用户。
- **AndroidKeyStore 中的 ECDSA 提供程序支持。** [[Android]] 现在有一个允许使用 [[ECDSA]] 和 [[DSA]] 算法的密钥库提供程序。
- **设备监测警告。** 如果有任何可能允许监测加密网络流量的证书添加到设备证书库中，Android 都会向用户发出警告。
- **FORTIFY_SOURCE。** Android 现在支持 [[FORTIFY_SOURCE]] 第 2 级，并且所有代码在编译时都会受到这些保护。FORTIFY_SOURCE 已得到增强，能够与 [[Clang]] 配合使用。
- **证书锁定。** Android 4.4 能够检测安全的 [[SSL]]/[[TLS]] 通信中是否使用了欺诈性 Google 证书，并且能够阻止这种行为。
- **安全修复程序。** Android 4.4 中还包含针对 Android 特有漏洞的修复程序。有关这些漏洞的信息已提供给“开放手机联盟”([[Open Handset Alliance]]) 成员，并且 Android 开源项目中提供了相应的修复程序。为了提高安全性，部分搭载更低版本 Android 系统的设备可能也会包含这些修复程序。