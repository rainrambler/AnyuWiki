- 差分隐私是隐私的正式定义，要求任何统计分析的输出都不会显示数据集中特定于个人的信息。算法通常通过向输入数据（局部差分隐私）或它产生的输出（全局差分隐私）添加噪声来实现差分隐私。
- 差分隐私是针对 Irit Nisur 和 Kobbi Nissim 2003 年的一篇论文而开发的，该论文确立了信息恢复的基本规律：对统计模型的过多查询的过度准确回答可以实现数据集恢复。因此，为了使用于构建模型的数据成为私有数据，该模型必然在某种程度上是不准确的。噪声量必须谨慎选择：太少，数据集将不是私有的，太多，输出将不准确以至于无用。这是**隐私效用的权衡**。
- 隐私效用权衡是通过Ɛ-差分隐私的概念形式化的。查询模型会泄漏有关数据集的信息，并且信息泄漏量随着查询次数的增加而增加。参数Ɛ 量化了这种泄漏，被称为隐私预算。如果超出预算，用户将停止执行进一步的查询。等效地，Ɛ 可以被认为是针对模型执行的查询的结果与针对已从数据集中省略个体的模型执行的相同查询的结果之间的最大允许差异。
- **采纳的风险：**
	- 为隐私预算选择合适的有价值的通常具有挑战性且高度特定于上下文；
	- 对于较小的子群体，噪声引入的不准确性将更加明显。 例如，美国人口普查局使用差异隐私的批评者认为，这会导致对当地人口统计数据的不准确理解，这可能导致社区受到基于该数据做出的政策决策的不利影响。
- https://cdeiuk.github.io/pets-adoption-guide/what-are-pets/