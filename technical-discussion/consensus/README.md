# 共识机制

要理解 Monad 的共识机制，需要了解以下几个关键点：

* [MonadBFT 共识机制](monadbft.md)： Monad 的共识机制，用于在部分同步条件下就任意有效载荷达成一致，同时保持拜占庭容错。
* [共享内存池](shared-mempool.md)： 定义对共识有效载荷的重大优化：通过哈希值引用交易，并确保交易提前通过 Mempool 传播。
* [延迟执行](deferred-execution.md)： 对达成共识的过程进行重大优化，将执行移出共识的热路径。
* [运输成本和储备金余额](carriage-cost-and-reserve-balance.md)： 定义交易定价的行为变化，这是为了防止垃圾交易攻击，因为共识是在延迟执行的情况下达成的。
