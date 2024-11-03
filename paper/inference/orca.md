


这篇论文是关于一个名为ORCA的分布式服务系统，它专门为基于Transformer的生成模型设计。以下是论文的主要内容概述：

1. **背景与动机**：
   - 大型基于Transformer的模型（如GPT-3）在生成任务中表现出色，但现有的推理服务系统在处理这类模型时存在性能瓶颈。这些模型需要多次迭代来生成每个输出令牌，而现有系统在处理多迭代请求时效率不高。

2. **主要问题**：
   - 现有系统在处理请求时，通常是按批次处理，这导致一些请求在批次中提前完成但无法及时返回给客户端，增加了延迟。同时，新到达的请求需要等待当前批次完全处理完毕，增加了排队时间。

3. **解决方案**：
   - **迭代级调度（Iteration-level Scheduling）**：提出一种新的调度机制，调度执行时以迭代为单位，而不是整个请求。这样，每次迭代后，可以立即处理新到达的请求，减少等待时间。
   - **选择性批处理（Selective Batching）**：在应用批处理和迭代级调度时，只对选定的操作应用批处理。这样可以在不同的操作中灵活地处理请求，避免因不同请求处理不同数量的令牌而导致的批处理问题。

4. **ORCA系统**：
   - ORCA是一个分布式服务系统，实现了上述两种技术。它还采用了模型并行化策略（如层内和层间模型并行化），以支持大规模模型。
   - ORCA的设计包括一个请求池、调度器和执行引擎。调度器负责从请求池中选择请求，执行引擎则负责执行模型的迭代。

5. **评估**：
   - 使用GPT-3模型进行评估，结果显示ORCA在延迟和吞吐量方面显著优于NVIDIA FasterTransformer。具体来说，ORCA在相同延迟水平下，吞吐量提高了36.9倍。

6. **结论**：
   - ORCA通过迭代级调度和选择性批处理，为基于Transformer的生成模型提供了一个高效、低延迟的服务系统。这种方法在处理大规模模型时表现出色，能够显著提高服务的吞吐量和响应速度。

论文的主要贡献在于提出了一种新的调度和批处理机制，解决了现有系统在处理基于Transformer的生成模型时的性能问题。



第三章 - 重点







