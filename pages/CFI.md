- 从 2016 年开始，Android 上大约 86% 的漏洞与内存安全相关。大多数漏洞被攻击者所利用，他们会改变应用的正常控制流，获取遭利用的应用的所有权限来执行任意恶意活动。[控制流完整性 (CFI)](https://clang.llvm.org/docs/ControlFlowIntegrity.html) 是一种安全机制，它不允许更改已编译二进制文件的原始控制流图，因而执行此类攻击变得异常困难。
- 在 Android 8.1 中，我们在媒体堆栈中启用了 [[LLVM]] 的 CFI 实现。在 Android 9 中，我们在更多组件以及内核中启用了 CFI。系统 CFI 默认处于启用状态，但内核 CFI 需要您手动启用。
- LLVM 的 CFI 需要使用[链接时优化 (LTO)](https://llvm.org/docs/LinkTimeOptimization.html)
   进行编译。[[LTO]] 会一直保留对象文件的 LLVM 位码表示法直至链接时，以便编译器更好地推断可以执行哪些优化。启用 LTO 可缩减最终二进制文件的大小并提高性能，但会增加编译时间。在 [[Android]] 上进行测试时，结合使用 LTO 和 CFI 对代码大小和性能开销的影响微乎其微；在少数情况下，这两者都会有所改善。
- Ref:
- https://source.android.google.cn/docs/security/test/cfi