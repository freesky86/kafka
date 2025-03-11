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

2. 启动 Kafka Server   
打开一个新的 CMD 窗口，同样进入 Kafka 目录。
运行以下命令启动 Kafka：bin\windows\kafka-server-start.bat config\server.properties   
默认配置下，Kafka 监听 9092 端口。保持这个窗口运行。

3. （可选）调整配置    
如果需要自定义配置，可以编辑 config\server.properties：

    listeners=PLAINTEXT://localhost:9092：指定监听地址。
    log.dirs=D:/kafka/kafka-logs：指定日志存储路径（路径用斜杠 /，而不是反斜杠 \）。
   
## 测试 Kafka
1. 创建主题（Topic）    
打开新 CMD 窗口，进入 Kafka 目录。
创建一个名为 test 的主题：
bin\windows\kafka-topics.bat --create --topic test --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1     
验证主题：
bin\windows\kafka-topics.bat --list --bootstrap-server localhost:9092    
会显示上面创建的主题test

2. 启动生产者（Producer）   
在新 CMD 窗口中运行：
bin\windows\kafka-console-producer.bat --topic test --bootstrap-server localhost:9092    
输入消息（每行一条），例如 Hello Kafka，按 Enter 发送。

3. 启动消费者（Consumer）    
在另一个 CMD 窗口中运行：  
bin\windows\kafka-console-consumer.bat --topic test --bootstrap-server localhost:9092 --from-beginning    
你会看到生产者发送的消息显示在这里。   

## 关闭 Kafka    
按 Ctrl+C 依次关闭消费者、生产者、Kafka Server 和 ZooKeeper 的 CMD 窗口。  
确保所有进程都停止，避免端口占用。   

## 注意事项    
1. 路径问题    
Windows 下路径分隔符可能导致问题，建议在配置文件中使用 / 而非 \。  
2. 防火墙    
如果遇到连接问题，检查 Windows 防火墙是否阻止了 2181（ZooKeeper）或 9092（Kafka）端口。  
3. 长期使用    
单机模式仅适合测试。生产环境建议使用 Docker 或在 Linux 上部署 Kafka 集群。  


   

 
