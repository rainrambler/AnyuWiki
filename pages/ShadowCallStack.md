- ShadowCallStack (SCS) 是一种 [LLVM 插桩](https://clang.llvm.org/docs/ShadowCallStack.html)模式，可将函数的返回地址保存到非叶函数的函数 prolog 中单独分配的 **ShadowCallStack**，并从函数 epilog 中的 ShadowCallStack 加载返回地址，从而防止返回地址覆盖（比如堆栈缓冲区溢出）。
- See: [[LLVM]]
-
- https://source.android.google.cn/docs/security/test/shadow-call-stack