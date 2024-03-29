- Android 4.4 及更高版本支持通过可选的 device-mapper-verity (dm-verity) 内核功能进行启动时验证，以便对块存储设备进行透明的完整性检查。dm-verity 有助于阻止可以持续保有 Root 权限并入侵设备的持续性 Rootkit。验证启动功能有助于 Android 用户在启动设备时确定设备状态与上次使用时是否相同。
- 具有 Root 权限的可能有害的应用 (PHA) 可以躲开检测程序的检测，并以其他方式掩蔽自己。可以获取 Root 权限的软件就能够做到这一点，因为它通常比检测程序的权限更高，从而能够“欺骗”检测程序。
- 通过 dm-verity 功能，您可以查看块设备（文件系统的底部存储层），并确定它是否与预期配置一致。该功能是利用加密哈希树做到这一点的。对于每个块（通常为 4k），都有一个 SHA256 哈希。
- https://source.android.google.cn/security/verifiedboot/dm-verity