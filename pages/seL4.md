- L4是第二代微内核（[[Microkernel]]）的几种实现的统称。
- 2006 年，[[NICTA]] 小组开始从头开始设计名为 seL4 的第三代微内核，旨在为高度安全和可靠的系统提供基础，以满足通用标准([[Common Criteria]])等安全要求。从一开始，开发的目标就是对内核进行形式化验证([[Formal verification]])。为了轻松满足有时相互冲突的性能和验证要求，该团队使用了一个中间软件流程，该流程从用 Haskell 编写的可执行规范开始。seL4 使用基于能力的安全访问控制([[Capability-based security]])来启用关于对象可访问性的正式推理。
- 功能正确性的正式证明([[Formal proof]])于 2009 年完成。该证明提供了内核的实现与其规范正确的保证，并暗示它没有实现错误，例如死锁、活锁、缓冲区溢出、算术异常或使用未初始化的变量。seL4 号称是第一个经过验证的通用操作系统内核。
- seL4 采用了一种新颖的内核资源管理方法，将内核资源的管理导出到用户级别，并使它们受到与用户资源相同的基于能力的访问控制。这个模型也被 [[Barrelfish]] 采用，简化了关于隔离属性的推理，并且是后来证明 seL4 强制执行完整性和机密性的核心安全属性的推动力。NICTA 团队还证明了从编程语言 C 到可执行机器代码的翻译的正确性，使编译器脱离了 seL4 的可信计算库([[Trusted computing base]])。这意味着高级安全证明适用于内核可执行文件。seL4 还是第一个发布的保护模式操作系统内核，具有完整且可靠的最坏情况执行时间 (WCET) 分析，这是其在硬实时计算([[Real-time computing]])中使用的先决条件。
- 2014 年 7 月 29 日，NICTA 和 General Dynamics C4 Systems 宣布，带有端到端证明的 seL4 现已在开源许可下发布。内核源代码和证明在 GNU 通用公共许可证版本 2 (GPLv2) 下获得许可，并且大多数库和工具都在 BSD 2 条款下。2020 年 4 月，宣布在 Linux 基金会的保护下创建 seL4 基金会，以加速 seL4 的开发和部署。
- 研究人员表示，尽管提供了更可靠的结果，但正式软件验证的成本低于设计传统“高保证”软件的成本。具体来说，在 seL4 的开发过程中，一行代码的成本估计约为 400 美元，而传统的高保证系统则为 1,000 美元。
- 在美国国防高级研究计划局 (DARPA) 高保证网络军事系统 (HACMS) 计划下，NICTA 与项目合作伙伴罗克韦尔柯林斯、伽罗瓦公司、明尼苏达大学和波音公司一起开发了一种使用 seL4 的高保证无人机，以及其他保证工具和软件，并计划将技术转移到波音公司正在开发的可选驾驶的自主波音 AH-6 无人小鸟直升机上。 HACMS 技术的最终演示于 2017 年 4 月在弗吉尼亚州斯特林举行。DARPA 还根据 John Launchbury 博士发起的一项计划资助了几项与 seL4 相关的小型企业创新研究 (SBIR) 合同。获得与 seL4 相关的 SBIR 的小型企业包括：DornerWorks、Techshot、Wearable Inc、Real Time Innovations 和 Critical Technologies。
-