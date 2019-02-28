# spark 和hadoop区别
  hadoop 缺点：
    MapReduce设计上的约束比较适合处理离线数据，在实时查询和迭代计算存在很多不足
    迭代支持
    中间数据需要输出到硬盘存储，产生较高的延迟
  spark 基于apache顶级开源项目，快速、通用的大规模数据处理引擎，和hadoop的MapReduce计算框架类似，相对于MapReduce,
    spar

  # 底层文件存储系统
    HDFS
    Amazon S3
    Hypertable
  # 资源管理
    SPARK SQL 提供SQL查询
    MLlib提供机器学习
    GraphX提供计算服务
    Spark Streaming 将流计算分解一系列批处理
