GTID:
  全局事务标识符，MySQL5.6，每个事务在同一个节点不会出现多次
  每一个事务在集群中具有唯一性
  根据GTID快速知道事务最初在那个实例上提交
  根据GTID搭建主从复制更加简单，确保每个事务只会被执行
  基于GTID，更方便实现Replication的failover
  MySQL组复制完全依赖GTID

  组成部分：
    GTID = source_id:sequence_id
          source_id是源服务器的唯一标识，通常使用服务器的server_uuid表示source_id
          sequence_id是在事务提交时由系统顺序分配一个序列号
