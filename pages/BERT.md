- 根据不同的任务，一个语言模型可能只使用编码器部分，或只使用解码器部分，或两者都使用。这种区分的典型例子是：
	- BERT模型，它代表了变形器的双向编码器表示法（Bidirectional Encoder Representations from Transformers）。顾名思义，它只使用变形器的编码器部分，它最擅长对给定的输入文本进行任何类型的预测或分类任务。
	- [[GPT]]模型，代表生成性预训练的变形器。它是纯解码器，正如其名称所示，最适合于涉及生成新文本的任务。
- https://arxiv.org/abs/1810.04805
- BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding
-