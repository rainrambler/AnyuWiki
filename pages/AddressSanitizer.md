- _警告：在 [[Android 11]] 之后的 [[AOSP]] master 中，弃用了 arm64 上的平台开发 ASan，改为使用 [[HWASan]]。_
- AddressSanitizer ([[ASan]]) 是一种基于编译器的快速检测工具，用于检测原生代码中的内存错误。
- ASan 可以检测以下问题：
	- 堆栈和堆缓冲区上溢/下溢
	- 释放之后的堆使用情况
	- 超出范围的堆栈使用情况
	- 重复释放/错误释放
- #Android 10 和 [[AArch64]] 上的 AOSP master 分支支持硬件加速 ASan ([[HWASan]])，这是一种 RAM 开销更小、检测到的错误范围更大的类似工具。除了 ASan 可以检测到的错误之外，HWASan 还可以检测返回之后的堆栈使用情况。
-