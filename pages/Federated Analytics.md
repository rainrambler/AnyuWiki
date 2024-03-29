- 联邦分析是针对分散数据执行计算机程序的范例。这涉及将程序上传到数据所在的服务器或设备的一方，在服务器或设备上执行该程序并在原地使用数据，并将结果传回给发起方。这样，就不会直接向当事人透露任何数据。
- 联邦分析的一个子集是联邦学习([[Federated Learning]])，它涉及在分布式数据集上训练机器学习模型。这个想法是使用本地数据直接在用户的设备上训练本地模型，然后让设备彼此共享结果模型的权重，以便确定新的全局模型。
- 这可以是集中式联合学习，其中中央服务器负责协调参与设备的操作（如下所示），也可以是分散式联合学习，其中参与设备相互协调。在任何一种情况下，关键特性是用户数据永远不会离开设备，因为只有模型权重会被传达。
- 攻击者可以从这些权重中推断出用户信息，并且通常会结合机制（例如下面讨论的差分隐私）来缓解这种情况。
- 需要考虑的限制
	- 尽管联合分析不提供对数据的直接访问，但有可能从分析的输出中推断出有关数据集中个人的信息。 以不同的隐私方式执行分析是降低这种风险的一种方法。
	- 无法直接访问数据会使开发、测试和故障排除代码变得更加困难。 应该共享远程数据库使用的架构和标准的详细信息以帮助缓解这种情况，以及开发人员可以用来验证其代码功能的虚拟数据。
	- 训练机器学习模型的计算成本很高，并且通常使用 GPU 等专用硬件进行加速。 在联邦学习中，您可能无法控制将在其上执行训练的远程硬件，这可能会限制您可以通过这种方式构建的模型类型。
- https://cdeiuk.github.io/pets-adoption-guide/what-are-pets/