# TX-LCN分布式事务解决方案

分布式事务解决是指，分布式环境下，各个微服务的本地事务做到同步，组合起来作为分布式原子事务，期望各个本地事务做到全部成功或全部失败。

#### 为什么会有本地事务与分布式事务之分？
几个协作的微服务，在调用过程中，一些本地事务成功了，某个本地事务失败，根据分布式事务要求，需要其它本地事务也要失败。

#### TX-LCN是怎样解决这个问题的？
一次分布式事务下，各个微服务的本地事务注册到一个事务管理服务中，在没有发生失败的本地事务情况下，统一做提交事务，有失败的情况，对所有事务做回滚。

#### TX-LCN这样解决问题为什么可行？
解决方案原理图如下：
![TC Arch](https://raw.githubusercontent.com/codingapi/tx-lcn/docs/docs/img/tc.png)
TC Logic
![TM Arch](https://raw.githubusercontent.com/codingapi/tx-lcn/docs/docs/img/tm.png)
TM Logic