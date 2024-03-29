- BoundsSanitizer
	- Android 10 在蓝牙和编解码器中部署了 [[BoundsSanitizer]] ([[BoundSan]])。BoundSan 使用 [[UBSan]] 的边界排错程序。
- 只执行内存
	- 默认情况下，[[AArch64]] 系统二进制文件的可执行代码部分会被标记为只执行（不可读取），作为应对即时代码重用攻击的安全强化缓解方法。
- 整数溢出排错功能
	- Android 10 在软件编解码器中启用了整数溢出排错功能 ([[IntSan]])。
- Scudo
	- [[Scudo]] 是一个动态的用户模式内存分配器，旨在提高遇到**堆相关漏洞**时的复原能力。它提供了标准 C 分配和取消分配基元，以及 C++ 基元。
- ShadowCallStack
	- ShadowCallStack (SCS) 是一种 [[LLVM]] 插桩模式，可将函数的返回地址保存到非叶函数的函数 prolog 中单独分配的 ShadowCallStack 实例，并从函数 epilog 中的 ShadowCallStack 实例加载返回地址，从而防止返回地址覆盖（比如堆栈缓冲区溢出）。
- OEMCrypto
	- Android 10 使用 OEMCrypto API 版本 15。
- WPA3 和 Wi-Fi Enhanced Open
	- Android 10 添加了对 Wi-Fi Protected Access 3 ([[WPA3]]) 和 Wi-Fi Enhanced Open 安全标准的支持，可更好地保护隐私，更稳健地防御已知攻击。
- 模块化系统组件
	- Android 10 采用模块化方式来处理一些 Android 系统组件，使其能够在 Android 的常规发布周期外的时间进行更新。
		- [[Conscrypt]]
		- [[DocumentsUI]]
		- [[PermissionController]]
- 延长设备解锁时间
	- 可信代理是 [[Smart Lock]] 等三重身份验证机制使用的底层机制，只能在 Android 10 中延长解锁时间。可信代理无法再解锁已锁定的设备，并且最多只能将设备解锁状态维持四个小时。
- 人脸识别身份验证
- 1. 安全相机帧
  2. 集成认证（网上银行等）
-
- ### 隐私
- 后台**位置权限**（`ACCESS_BACKGROUND_LOCATION`），设备位置信息限制：为了让用户更好地控制应用对位置信息的访问权限，Android 10 引入了 ACCESS_BACKGROUND_LOCATION 权限。
- 系统会增加针对从**后台启动** [[Activity]] 的限制。此项行为变更有助于最大限度地减少对用户造成的干扰，并且可以让用户更好地控制其屏幕上显示的内容。
- **相机元数据**：Android 10 更改了 [getCameraCharacteristics()](https://developer.android.google.cn/reference/android/hardware/camera2/CameraManager#getCameraCharacteristics(java.lang.String)) 方法默认返回的信息的广度。具体而言，您的应用必须具有 [CAMERA](https://developer.android.google.cn/reference/android/Manifest.permission#CAMERA) 权限才能访问此方法的返回值中可能包含的设备特定元数据。
- **剪贴板数据**：对于 Android 10 或更高版本，除非您的应用是默认输入法 ([[IME]]) 或是目前聚焦的应用，否则它无法访问剪贴板中的数据。
- **外部存储**设备访问限制
	- 无需权限，仅能访问：
		- 特定于应用的目录中的文件（使用 [getExternalFilesDir()](https://developer.android.google.cn/reference/android/content/Context#getExternalFilesDir(java.lang.String)) 访问）。
		- 应用创建的照片、视频和音频片段（通过[媒体库](https://developer.android.google.cn/training/data-storage/files/media)访问）。
- **随机分配 [[MAC]] 地址**：默认情况下，在搭载 Android 10 或更高版本的设备上，系统会传输随机分配的 MAC 地址。
- 不可重置的**设备标识符**：从 Android 10 开始，应用必须具有 READ_PRIVILEGED_PHONE_STATE 特许权限才能访问设备的不可重置标识符（包括 [[IMEI]] 和序列号）。
- **身体活动**识别: Android 10 针对需要检测用户步数或对用户的身体活动（例如步行、骑车或坐车）进行分类的应用引入了 android.permission.[[ACTIVITY_RECOGNITION]] 运行时权限。此项权限旨在让用户了解设备传感器数据在“设置”中的使用方式。
	- 除非用户已向应用授予此权限，否则 [[Google Play]] 服务中的一些库（例如 [[Activity Recognition]] API 和 [[Google Fit]] API）不会提供结果。
	- 设备上要求您声明此权限的内置传感器只有计步器和步测器传感器。
- **/proc/net** 文件系统限制
	- 在搭载 Android 10 或更高版本的设备上，应用无法访问 /proc/net，包括与设备的网络状态相关的信息。需要访问此信息的应用（如 [[VPN]]）应使用 [[NetworkStatsManager]] 或 [[ConnectivityManager]] 类。
- 从界面中移除了**权限组**
	- 从 Android 10 开始，应用无法在界面中查询权限的分组方式。
- 移除了联系人关系密切程度
	- 从 Android 10 开始，平台不再记录联系人的关系密切程度信息。因此，如果您的应用对用户的联系人进行搜索，系统将不会按互动频率对搜索结果排序。
	- 有关 [[ContactsProvider]] 的指南包含一项说明特定字段和方法已废弃的声明（从 Android 10 开始，这些字段和方法在所有设备上已作废）。
- 限制对**屏幕内容**的访问
	- 为了保护用户的屏幕内容，Android 10 更改了 READ_FRAME_BUFFER、CAPTURE_VIDEO_OUTPUT 和 CAPTURE_SECURE_VIDEO_OUTPUT 权限的作用域，从而禁止以静默方式访问设备的屏幕内容。从 Android 10 开始，这些权限只能通过签名访问。
	- 需要访问设备屏幕内容的应用应使用 [[MediaProjection]] API，此 API 会显示要求用户同意访问的提示。
- USB **设备序列号**
	- 如果您的应用以 Android 10 或更高版本为目标平台，则该应用只能在用户授予其访问 [[USB]] 设备或配件的权限后才能读取序列号。
- Wi-Fi
	- 以 Android 10 或更高版本为目标平台的应用无法启用或停用 Wi-Fi。[[WifiManager]].setWifiEnabled() 方法始终返回 false。
	- 如果您需要提示用户启用或停用 Wi-Fi，请使用设置面板。
- 对直接访问已配置的 Wi-Fi 网络实施了限制
	- 为了保护用户隐私，只有系统应用和设备政策控制者 (DPC) 支持手动配置 [[Wi-Fi]] 网络列表。给定 DPC 可以是设备所有者，也可以是资料所有者。
	- 如果应用以 Android 10 或更高版本为目标平台，并且应用不是系统应用或 DPC，则下列方法不会返回有用数据：
		- getConfiguredNetworks() 方法始终返回空列表。
		- 每个返回整数值的网络操作方法（addNetwork() 和 updateNetwork()）始终返回 -1。
		- 每个返回布尔值的网络操作（removeNetwork()、reassociate()、enableNetwork()、disableNetwork()、reconnect() 和 disconnect()）始终返回 false。
-
- Prev: [[Android 9]]
- Next: [[Android 11]]