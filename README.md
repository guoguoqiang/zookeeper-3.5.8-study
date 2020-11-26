# 源码修改
源码导入idea后，org.apache.zookeeper.Version类会报错，需要建一个辅助类
```
package org.apache.zookeeper.version;

public interface Info {
    int MAJOR = 1;
    int MINOR = 0;
    int MICRO = 0;
    String QUALIFIER = null;
    int REVISION = -1;
    String REVISION_HASH = "1";
    String BUILD_DATE = "2020-10-15";
}
```
1、将conf文件夹里的zoo_sample.cfg文件复制一份改名为zoo.cfg，将zoo.cfg文件位置配置到启动参数里

2、启动之前需要先将zookeeper-server项目里pom.xml文件里依赖的包(除了jline)的scope为provided这一行全部注释掉

3、将conf文件夹里的log4j.properties文件复制一份到zookeeper-server项目的 \target\classes 目录下，这样项目启动时才会打印日志


# 单机配置
参考 conf/zoo_.cfg 配置

idea 启动配置: 配置文件路径

Main class：
org.apache.zookeeper.server.quorum.QuorumPeerMain

program arguments: 
D:\my_project\zookeeper-release-3.5.8\conf\zoo_.cfg

working directory：D:\my_project\zookeeper-release-3.5.8


# 集群配置
1、创建data文件夹

2、在data文件夹下面创建zk1文件夹

3、在zk1文件夹下面创建 myid 文件 里面写上数字1

4、复制zk1 创建 zk2和zk3 

5、修改zk2和zk3 myid文件 里面的数字为 2和3 

参考 conf/zoo_1.cfg、conf/zoo_2.cfg conf/zoo_3.cfg

idea 启动配置: 配置文件路径

Main class：
org.apache.zookeeper.server.quorum.QuorumPeerMain

program arguments: 
D:\my_project\zookeeper-release-3.5.8\conf\zoo_1.cfg

working directory：D:\my_project\zookeeper-release-3.5.8

另外2个 服务一样




program arguments: 
D:\my_project\zookeeper-release-3.5.8\conf\zoo_1.cfg


# 从源码里运行客户端(org.apache.zookeeper.ZooKeeperMain)


Main class: org.apache.zookeeper.ZooKeeperMain

program arguments: 
-server localhost:2181



