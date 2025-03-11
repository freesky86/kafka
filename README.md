# kafka
Spring Boot + kafka

# Windows安装使用
## 下载kafka   
https://kafka.apache.org/downloads   
 kafka_2.13-3.9.0.tgz   
其中 2.13是Scala版本，3.9.0是kafka版本    
解压成文件夹，注意路径不要太多，最多两层，像下面这样    
D:\kafka\kafka_2.13-3.9.0
## 安装和配置 Kafka
1. 启动 ZooKeeper
打开 CMD，进入 Kafka 解压目录（例如 D:\kafka\kafka_2.13-3.9.0）    
运行以下命令启动 ZooKeeper：
bin\windows\zookeeper-server-start.bat config\zookeeper.properties    
默认配置下，ZooKeeper 监听 2181 端口。保持这个窗口运行。
3. 启动 Kafka Server
4. 
 
