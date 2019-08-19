MFS
  MooseFS 容错功能的分布式文件系统
  分层的目录结构
  支持posix标准文件属性
  支持特殊文件
  支持ip和密码访问
  特性：
    高可用，副本数量
    高扩展性
    高可容错性
    数据一致性

  缺点：
    1.master服务器对主机要求比较高（映射文件后端访问路径）
    2.原数据比较复制时间比较长，3小时

  场景：
    1.大规模高并发的数据存储及访问
    2.大规模数据存储出来，如日志分析。小文件强调性能不强调使用HDFS
    3.使用尽量前端加CACHE
    参考文档：http://oldboy.blog.51cto.com/256140/736710

  架构设计方法





  主流分布式：
    CEPH：
    gulsterfs:
    hadoop HDFS:
    MogileFs:
    FastDFS:
    NFS:使用最多


  原理：
    管理服务器（master):
        分发用户请求，存储文件的metadata信息（包括文件的存放目录，属性)，类似于LVS负载均衡主服务器，不同的是lvs仅仅根据算法分发请求，而master根据内存的metadata信息分发请求，内存的信息会被实时写入到磁盘。这个master，只有一台处于激活工作的状态。

    元数据备份服务器（metadata backup servers 简写metalogger)
        备份管理服务器的master的变化的metadata信息日志文件，文件类型为changelog_ml.*mfs,便于主服务器出现问题，可经过简单操作恢复应用

    data servers(data)
        文件存储服务器（没有master 无法使用）

  配置选择物理资源：
    1.master 中除了1百万哥文件需要300M内存
  演示环境配置
    mfs master:10.0.0.7
    mfs backup:10.0.0.8
    data01:10.0.0.17
    data02:10.0.0.18
    data03:10.0.0.19
    mfs client:10.0.0.27
    mfs VIP:10.0.0.9
