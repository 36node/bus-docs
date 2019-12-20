# 系统架构

新能源监控平台旨在提供对大量乘用车和商用车进行安全监控、数据采集和统计分析，
为甲方后续的业务提供数据支撑。

本文旨在描述新能源监控平台的系统架构。

## 技术原则

- 微服务
  - 尽可能服务无状态
  - 高内聚、低耦合的服务划分原则
- DevOps
  - 以`Docker`镜像方式交付
  - 运维文档即代码
  - 镜像优化，减少拉取时间
  - 使用 K8s 集群进行部署
- Restful API
  - 设计原则[中文参考](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
  - Query 的语法格式，[参考](https://github.com/36node/sketch/blob/master/packages/query-normalizr/README.md#query-in-route-qir)
  - Openapi 2.0，提供标准的 API 文档
  - 数据传输格式采用 `json`
- JWT
  - 加密通讯
  - 技术[参考](https://jwt.io)
- 前端技术原则
  - SPA 前后端分离
  - PWA 提升页面体验
  - 函数式编程
  - ES7, css-in-js

## 主要前端库

- webpack
- babel
- react
- redux
- saga
- styled-components
- antd
- normalizr
- lodash
- echarts
- @36node/sketch

## 主要后端库

后端主要采用的语言是 nodejs 和 go。

- koa2
- @36node/permit
- mongodb
- mysql
- flink
- spark/spark stream
- kafka
- hive
- hbase
- hdfs
- redis
- elasticsearch
- oos

## 大数据分析平台架构

数据通过多种协议接入，包括：

- 自定义 tcp 协议，例如 catl 的 rdb 协议
- 各个服务产生的日志通过 flume 接入
- 标准物联网组件可以通过 MQTT 接入
- 通过 HTTP 协议接收主动推送的数据
- 通过 Sqoop 等工具从 sql 数据库同步数据

数据经过 Kafka 消息队列分发到大数据处理中心，这里会分为流失处理和批处理两条线。流处理主要通过 Flink 和 Spark stream 来处理，批处理主要通过 Spark。
数据再 HDFS 和 HBASE 中沉淀，作为中期数据仓储，长期的数据仓库会存在 oos 中，具体根据不同的云厂商提供的类别定。

上层数据分析通过 Elasticsearch 接入热数据的方式实现，数据分析引擎计划采用 `Zeppelin`。部分热数据还会存到 Mysql 中，作为交换区数据。整体系统架构图如下：

￼![image](https://user-images.githubusercontent.com/1524745/59153667-3f196d00-8a92-11e9-817d-4301ccdc07fb.png)

## 服务架构

整个平台后端由 bus-log, bus-core, bus-chart, bus-tbox, bus-op 几个主要服务组成。

- bus-log: 车辆日志服务
- bus-realtime: 车辆实时数据服务
- bus-core: 核心服务，包括车辆的档案和车辆实时信息
- bus-chart: 图表服务，这里连接着大数据平台
- bus-tbox: 32960 接收端
- bus-op: 工单、报警、预警服务
- 总线服务: 利用 kafka 实现全局的异步总线，注意这里的部署配置一定要好

![image](https://user-images.githubusercontent.com/1524745/59156251-570ce300-8aca-11e9-952d-32f07b4994d8.png)
